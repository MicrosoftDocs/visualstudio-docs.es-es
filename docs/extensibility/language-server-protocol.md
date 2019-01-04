---
title: Información general sobre el protocolo de servidor Language | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b2329b54ba90a37e0d6d5e782e66c4af923a646
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828230"
---
# <a name="language-server-protocol"></a>Protocolo de servidor de lenguaje

## <a name="what-is-the-language-server-protocol"></a>¿Qué es el protocolo de servidor de lenguaje?

Compatibilidad enriquecida que las características de edición como auto-finalizaciones de código fuente o **ir a definición** para un lenguaje de programación en un editor o IDE es tradicionalmente muy difícil y llevar mucho tiempo. Normalmente requiere la escritura de un modelo de dominio (un escáner, un analizador, un comprobador de tipo, un generador y mucho más) en el lenguaje de programación del editor o IDE. Por ejemplo, el complemento de Eclipse CDT, que proporciona compatibilidad para C/C ++ en el IDE de Eclipse es escrito en Java desde del propio IDE de Eclipse está escrito en Java. Al seguir este enfoque, significaría implementar un modelo de dominio de C o C++ en TypeScript para Visual Studio Code y un modelo de dominio independiente en C# para Visual Studio.

Creación de modelos de dominio específico del lenguaje también es mucho más fácil si una herramienta de desarrollo puede volver a usar las bibliotecas específicas del lenguaje existentes. Sin embargo, estas bibliotecas se implementan normalmente en el lenguaje de programación mismo (por ejemplo, C o C++ dominios modelos se implementan en C/C ++). Integración de una biblioteca de C o C++ en un editor que se escriben en TypeScript es técnicamente posible pero difícil de hacer.

### <a name="language-servers"></a>Servidores de lenguaje

Otro enfoque consiste en ejecutar la biblioteca en su propio proceso y utilizan la comunicación entre proceso para comunicarse con ella. Los mensajes que envía y recibe un protocolo de formulario. El protocolo del servidor idioma (LSP) es el producto de estandarización de los mensajes intercambiados entre una herramienta de desarrollo y un proceso de servidor de lenguaje. Utilizar servidores de lenguaje o demons no es una idea nueva o novel. Editores, como Vim y Emacs haber hecho esto durante algún tiempo proporcionar compatibilidad con la semántica de finalización automática. El objetivo de lo LSP era simplificar a estos tipos de integraciones y proporcionan un marco útil para exponer las características de idioma a una variedad de herramientas.

Tener un protocolo común, permite la integración de características del lenguaje de programación en una herramienta de desarrollo sin mayores inconvenientes al volver a usar una implementación existente del modelo de dominio del idioma. Podría escribirse un lenguaje servidor back-end en PHP, Python o Java y lo LSP le permite integrar fácilmente en una variedad de herramientas. El protocolo funciona en un nivel de abstracción común para que una herramienta puede ofrecer servicios de lenguaje enriquecido sin necesidad de entender totalmente los matices específicos del modelo de dominio subyacente.

## <a name="how-work-on-the-lsp-started"></a>Cómo funcionan en lo LSP iniciado

El LSP ha evolucionado con el tiempo y hoy en día es en la versión 3.0. Inicia cuando el concepto de un servidor de lenguaje ha recogido OmniSharp para proporcionar características de edición enriquecidas para C#. Inicialmente, OmniSharp utiliza el protocolo HTTP con una carga JSON y se ha integrado en varios editores incluido [Visual Studio Code](https://code.visualstudio.com).

Aproximadamente al mismo tiempo, Microsoft empezó a trabajar en un servidor de lenguaje TypeScript, con la idea de la compatibilidad con TypeScript en editores, como Sublime Text y de Emacs. En esta implementación, un editor se comunica a través de stdin y stdout con el proceso de servidor de TypeScript y utiliza una carga JSON inspirado en el protocolo del depurador V8 de solicitudes y respuestas. El servidor de TypeScript se ha integrado en el complemento de TypeScript Sublime y VS Code para su edición enriquecida de TypeScript.

Después de tener integrada dos servidores en diferentes idiomas, el equipo de VS Code comenzó a explorar un protocolo de servidor de lenguaje común para los editores e IDE. Un protocolo común permite que un proveedor de lenguaje crear un servidor único lenguaje que puede utilizarse en diferentes IDE. Un consumidor de servidor de lenguaje solo tiene que implementar el cliente del protocolo de una vez. Esto produce una situación beneficiosa para el proveedor de lenguaje y el consumidor de lenguaje.

Se ha iniciado el protocolo de servidor de lenguaje con el protocolo utilizado por el servidor de TypeScript, expandirla con más características del lenguaje inspiradas en la API del lenguaje de VS Code. El protocolo está respaldado con JSON-RPC para la invocación remota debido a su simplicidad y las bibliotecas existentes.

El frente a un archivo de código de un prototipo del equipo el protocolo mediante la implementación de varios servidores de lenguaje linter que responden a las solicitudes a lint (Analizar) y devolver un conjunto de errores y advertencias detectadas. El objetivo era lint un archivo como las modificaciones del usuario en un documento, lo que significa que habrá muchas solicitudes de detección de errores durante una sesión del editor. Tenía sentido mantener un servidor de seguridad y la ejecución para que no fue necesario para cada edición de usuario se puede iniciar un nuevo proceso de detección de errores. Se han implementado varios servidores linter, incluido el código de VS ESLint y TSLint extensiones. Estos dos servidores linter se implementa en TypeScript/JavaScript y ejecutar en Node.js. Comparten una biblioteca que implementa la parte del cliente y servidor del protocolo.

## <a name="how-the-lsp-works"></a>Cómo funciona el LSP

Un servidor de lenguaje se ejecuta en su propio proceso, y herramientas como Visual Studio o VS Code se comuniquen con el servidor mediante el protocolo de lenguaje a través de JSON-RPC. Otra ventaja de que el servidor de lenguaje funciona en un proceso dedicado es que se evitan problemas de rendimiento relacionados con un modelo de proceso único. El canal de transporte real puede ser stdio, sockets, canalizaciones con nombre o nodo ipc si el cliente y el servidor están escritos en Node.js.

A continuación se muestra un ejemplo de cómo se comunican una herramienta y un servidor de idioma durante una rutina de sesión de edición:

![diagrama de flujo de LSP](media/lsp-flow-diagram.png)

* **El usuario abre un archivo (conocido como un documento) en la herramienta**: La herramienta notifica al servidor de lenguaje que un documento está abierto (' textDocument/didOpen'). De ahora en adelante, la verdad sobre el contenido del documento ya no está en el sistema de archivos pero se mantiene mediante la herramienta en la memoria.

* **El usuario realiza modificaciones**: La herramienta notifica al servidor sobre el cambio de documento (' textDocument/didChange') y la información semántica del programa se actualiza el servidor de lenguaje. Como en este caso, el servidor de lenguaje analiza esta información y notifica a la herramienta con los errores detectados y advertencias (' textDocument/publishDiagnostics').

* **El usuario ejecuta "Ir a definición" en un símbolo en el editor de**: La herramienta envía una solicitud de definición/textDocument con dos parámetros: (1) el identificador URI del documento y (2) la posición del texto desde donde se inició el ir a la solicitud de definición para el servidor. El servidor responde con el identificador URI del documento y la posición de la definición del símbolo dentro del documento.

* **El usuario cierra el documento (archivo)**: Se envía una notificación de ' textDocument/didClose' de la herramienta, que informa al servidor de lenguaje que el documento está ahora ya no en memoria y que el contenido actual es ahora actualizadas en el sistema de archivos.

En este ejemplo se muestra cómo se comunica el protocolo con el servidor de lenguaje en el nivel de características del editor como "Ir a definición", "Buscar todas las referencias". Los tipos de datos usados por el protocolo están editor o IDE 'tipos de datos' como el documento de texto abierto actualmente y la posición del cursor. Los tipos de datos no están en el nivel de un modelo de dominio programación de lenguaje que normalmente proporcionaría los árboles de sintaxis abstracta y los símbolos del compilador (por ejemplo, resolver tipos, espacios de nombres,...). Esto simplifica significativamente el protocolo.

Ahora Echemos un vistazo a la solicitud de definición/textDocument con más detalle. A continuación se muestran las cargas que vaya entre la herramienta de cliente y el servidor de lenguaje para la solicitud "Ir a definición" de un documento de C++.

Se trata de la solicitud:

```json
{
    "jsonrpc": "2.0",
    "id" : 1,
    "method": "textDocument/definition",
    "params": {
        "textDocument": {
            "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/use.cpp"
        },
        "position": {
            "line": 3,
            "character": 12
        }
    }
}
```

Se trata de la respuesta:

```json
{
    "jsonrpc": "2.0",
    "id": "1",
    "result": {
        "uri": "file:///p%3A/mseng/VSCode/Playgrounds/cpp/provide.cpp",
        "range": {
            "start": {
                "line": 0,
                "character": 4
            },
            "end": {
                "line": 0,
                "character": 11
            }
        }
    }
}
```

En retrospectiva, que describe los tipos de datos en el nivel del editor, en lugar de en el nivel del modelo de lenguaje de programación es uno de los motivos para el éxito del protocolo de servidor de lenguaje. Es mucho más sencillo estandarizar el URI de un documento de texto o una posición del cursor en comparación con un símbolos del compilador y de árbol de sintaxis abstracta la estandarización en diferentes lenguajes de programación.

Cuando un usuario está trabajando con diferentes lenguajes, VS Code inicia normalmente un servidor de lenguaje para cada lenguaje de programación. El ejemplo siguiente muestra una sesión donde el usuario trabaja en archivos de Java y SASS.

![Java y sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Capacidades

No todos los servidores de lenguaje pueden admitir todas las características definidas por el protocolo. Por lo tanto, el cliente y servidor anuncia su conjunto de características compatibles a través de "capabilities". Por ejemplo, un servidor anuncia que pueda controlar la solicitud de definición/textDocument, pero no puede atender la solicitud de "área de trabajo/symbol". De forma similar, los clientes pueden anunciar que son capaces de proporcionar ' a guardar' notificaciones antes de que se guarda un documento, para que un servidor puede calcular las ediciones de texto para dar formato automáticamente el documento modificado.

## <a name="integrating-a-language-server"></a>Integrar un servidor de lenguaje

La integración real de un servidor de idioma en una herramienta concreta no está definida por el protocolo de servidor de lenguaje y se deja a los implementadores de la herramienta. Algunas herramientas integran servidores de lenguaje de forma genérica por tener una extensión que puede iniciar y comunicarse con cualquier tipo de servidor de lenguaje. Otros, como VS Code, creación una extensión personalizada por el servidor de lenguaje, para que una extensión es aún capaz de proporcionar algunas características de lenguaje personalizado.

Para simplificar la implementación de clientes y servidores de lenguaje, hay bibliotecas o SDK para los componentes de cliente y servidor. Estas bibliotecas se proporcionan para distintos idiomas. Por ejemplo, hay un [módulo npm de cliente de lenguaje](https://www.npmjs.com/package/vscode-languageclient) para facilitar la integración de un servidor de idioma en una extensión de VS Code y otro [módulo npm de lenguaje server](https://www.npmjs.com/package/vscode-languageserver) para escribir en un servidor de lenguaje mediante Node.js. Se trata de la actual [lista](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) de bibliotecas de compatibilidad.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Mediante el protocolo de servidor de lenguaje en Visual Studio

* [Agregar una extensión del protocolo de servidor de lenguaje](adding-an-lsp-extension.md) -Obtenga información sobre cómo integrar un servidor de lenguaje en Visual Studio.
