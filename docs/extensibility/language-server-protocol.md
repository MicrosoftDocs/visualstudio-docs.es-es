---
title: "Información general sobre el protocolo de servidor Language | Documentos de Microsoft"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 79022af292161d30440a01749ecc929ce7f3b511
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="language-server-protocol"></a>Protocolo de servidor de idioma

## <a name="what-is-the-language-server-protocol"></a>¿Qué es el protocolo del servidor idioma?

Características de edición de apoyo enriquecidas como origen de código automática finalizaciones o **ir a definición** para un lenguaje de programación en un editor o IDE es tradicionalmente muy difíciles y requiere mucho tiempo. Normalmente es necesario escribir un modelo de dominio (un escáner, un analizador, el Comprobador de un tipo, un generador y mucho más) en el lenguaje de programación del editor o IDE. Por ejemplo, el complemento de Eclipse CDT, que proporciona compatibilidad con C o C++ en el IDE Eclipse se escribe en Java desde el IDE Eclipse sí mismo está escrito en Java. Después de este enfoque, significaría implementar un modelo de dominio de C o C++ en TypeScript para código de Visual Studio y un modelo de dominio independientes en C# para Visual Studio.

Creación de modelos de dominio específico de idioma también es mucho más fácil si una herramienta de desarrollo puede volver a usar bibliotecas existentes de específica del lenguaje. Sin embargo, estas bibliotecas se implementan normalmente en el lenguaje de programación mismo (por ejemplo, buena C/C++ dominio modelos se implementan en C/C ++). Integración de una biblioteca de C o C++ en un editor escrito en TypeScript es técnicamente posible pero difícil de hacer.

### <a name="language-servers"></a>Servidores de lenguaje

Otro enfoque consiste en ejecutar la biblioteca en su propio proceso y utilizan la comunicación entre procesos para comunicarse con él. Los mensajes enviados y hacia atrás forman un protocolo. El protocolo del servidor idioma (LSP) es el producto de normalización de los mensajes intercambiados entre una herramienta de desarrollo y un proceso de servidor de idioma. Uso de servidores de lenguaje o demons no es una idea nueva o novel. Editores, como Vim y ha realizado Emacs esto durante algún tiempo proporcionar compatibilidad con la semántica de finalización automática. El objetivo de lo LSP fue simplificar a este tipo de integraciones y proporcionan un marco útil para exponer las características de idioma a una variedad de herramientas.

Tener un protocolo común permite la integración de características de lenguaje de programación en una herramienta de desarrollo con una mínima complicación volviendo a una implementación existente de un modelo de dominio del idioma. Se podría escribir un lenguaje servidor back-end de PHP, Python o Java y lo LSP le permite integrar fácilmente en una variedad de herramientas. El protocolo funciona en un nivel de abstracción común para que una herramienta puede ofrecer servicios de lenguaje enriquecida sin necesidad de conocer perfectamente los matices específicos del modelo de dominio subyacente.

## <a name="how-work-on-the-lsp-started"></a>Cómo funcionan en el LSP iniciado

El proveedor de servicios Lingüísticos ha evolucionado a lo largo del tiempo y hoy en día se encuentra en la versión 3.0. Inicia cuando el concepto de un servidor de lenguaje ha recogido OmniSharp para proporcionar características de edición enriquecidas en C#. Inicialmente, OmniSharp utiliza el protocolo HTTP con una carga JSON y se ha integrado en varios editores incluido [código de Visual Studio](https://code.visualstudio.com).

Aproximadamente al mismo tiempo, Microsoft comenzó a trabajar en un servidor de idioma de TypeScript, con la idea de admitir TypeScript en editores como Emacs y texto fundamentales. En esta implementación, un editor se comunica a través de stdin/stdout con el proceso de servidor de TypeScript y usa una carga JSON inspirados en el protocolo de depurador V8 para las solicitudes y respuestas. El servidor de TypeScript se ha integrado en el complemento TypeScript fundamentales y el código de VS para TypeScript completa de edición.

Después de tener en dos servidores de distintos idiomas integrado, el equipo frente a código comenzó a explorar un protocolo de servidor de lenguaje común para los editores e IDE. Un protocolo común permite que un proveedor de lenguaje crear un servidor de idioma único que puede ser utilizado por los IDE diferentes. Un consumidor de servidor de idioma solo tiene que implementar el cliente del protocolo de una vez. Esto da como resultado una situación provechosas para el proveedor de lenguaje y el consumidor de lenguaje.

Trabajar con el protocolo de lenguaje utilizado por el servidor de TypeScript, era más general e independientes del idioma. El protocolo era con más características de lenguaje mediante la API del lenguaje de código de VS para obtener ideas. El protocolo en sí se copia con JSON-RPC para la invocación remota debido a sus bibliotecas de simplicidad y soporte técnico para muchos lenguajes de programación.

El equipo de VS Code dogfooded el protocolo mediante la implementación de varios servidores de lenguaje linter. Un servidor de lenguaje linter responde a las solicitudes para quitar un archivo (Analizar) y devuelve un conjunto de errores y advertencias detectadas. El objetivo era para quitar un archivo como las modificaciones de usuario en un documento, lo que significa que habrá muchas solicitudes de linting durante una sesión del editor. Tenía sentido para mantener un servidor de seguridad y ejecutándose para que un nuevo proceso linting no necesita que se iniciará para cada edición de usuario. Se han implementado varios servidores de linter, incluido el código de VS extensiones ESLint y TSLint. Estos dos servidores linter tanto implementa en TypeScript/JavaScript y ejecutar en Node.js. Comparten una biblioteca que implementa la parte del cliente y el servidor del protocolo.

## <a name="how-the-lsp-works"></a>Cómo funciona el LSP

Un servidor de idioma se ejecuta en su propio proceso, y herramientas como Visual Studio o código frente a comunican con el servidor mediante el protocolo de lenguaje a través de JSON-RPC. Otra ventaja del servidor idioma funcionando en un proceso dedicado es que se evitan los problemas de rendimiento relacionados con un modelo de proceso único. El canal de transporte real puede ser stdio, sockets, canalizaciones con nombre o nodo ipc si el cliente y el servidor se escriben en Node.js.

A continuación se muestra un ejemplo de cómo se comunican una herramienta y un servidor de idioma durante una rutina de sesión de edición:

![diagrama de flujo de LSP](media/lsp-flow-diagram.png)

* **El usuario abre un archivo (conocido como un documento) en la herramienta**: la herramienta notifica al servidor de idioma que un documento esté abierto (' textDocument/didOpen'). De ahora en adelante, la verdad sobre el contenido del documento ya no está en el sistema de archivos pero se conserva por la herramienta en la memoria.

* **El usuario realice modificaciones**: la herramienta notifica al servidor sobre el cambio de documento (' textDocument/didChange') y la información semántica del programa se actualiza mediante el servidor de idioma. Cuando esto ocurre, el servidor de idioma analiza esta información y notifica a la herramienta con los errores detectados y advertencias (' textDocument/publishDiagnostics').

* **El usuario ejecuta "Ir a definición" en un símbolo en el editor de**: la herramienta envía una solicitud de definición/textDocument con dos parámetros: (1) el identificador URI del documento y (2) la posición del texto desde donde se inició el ir a la solicitud de definición para el servidor. El servidor responde con el identificador URI del documento y la posición de la definición del símbolo dentro del documento.

* **El usuario cierra el documento (archivo)**: se envía una notificación de ' textDocument/didClose' de la herramienta, que informa el servidor de idioma que el documento está ya no está en memoria y que el contenido actual es ahora actualizadas en el sistema de archivos.

Este ejemplo muestra cómo se comunica el protocolo con el servidor de idioma en el nivel de características del editor como "Ir a definición", "Buscar todas las referencias". Los tipos de datos utilizados por el protocolo están editor o IDE 'tipos de datos' como el documento de texto abierto actualmente y la posición del cursor. Los tipos de datos no están en el nivel de un modelo de dominio lenguaje de programación que normalmente proporcionaría árboles de sintaxis abstracta y compilador símbolos (por ejemplo, resolver tipos, espacios de nombres,...). Esto simplifica considerablemente el protocolo.

Ahora Echemos un vistazo a la solicitud de definición/textDocument con más detalle. A continuación se muestran las cargas que vaya entre la herramienta de cliente y el servidor de idioma para la solicitud "Ir a definición" de un documento de C++.

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

En retrospectiva, que describe los tipos de datos en el nivel del editor, en lugar de hacerlo en el nivel del modelo de lenguaje de programación es una de las razones para el éxito del protocolo de servidor de idioma. Es mucho más fácil estandarizar un identificador URI del documento de texto o una posición del cursor en comparación con la normalización de un árbol y compilador símbolos de sintaxis abstracta a través de diferentes lenguajes de programación.

Cuando un usuario está trabajando con diferentes idiomas, frente a código normalmente se inicia un servidor de idioma para cada lenguaje de programación. En el ejemplo siguiente se muestra una sesión donde el usuario trabaja en los archivos de Java y SASS.

![Java y sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Capacidades

No todos los servidores de idioma pueden admitir todas las funciones definidas por el protocolo. Por lo tanto, el cliente y el servidor presenta su conjunto de características compatibles a través de "capacidades". Por ejemplo, un servidor anuncia que puede controlar la solicitud ' textDocument/definición', pero no puede controlar la solicitud 'área de trabajo/símbolo'. De igual forma, los clientes pueden anunciar que son capaces de proporcionar ' a punto de guardar' notificaciones antes de que se guarda un documento, para que un servidor puede calcular ediciones de texto para dar formato automáticamente el documento modificado.

## <a name="integrating-a-language-server"></a>Integrar un servidor de idioma

La integración real de un servidor de idioma en una herramienta concreta no está definida por el protocolo de servidor de idioma y se deja a los implementadores que la herramienta. Algunas herramientas integran servidores de lenguaje genéricamente y que tengan una extensión que se puede iniciar y hablar con cualquier tipo de servidor de idioma. Otros, como código de VS, crean una extensión personalizada por cada servidor de idioma, para que una extensión está siendo capaz de proporcionar algunas características de lenguaje personalizado.

Para simplificar la implementación de clientes y servidores de lenguaje, hay bibliotecas o SDK para las partes de cliente y servidor. Estas bibliotecas se proporcionan para los distintos idiomas. Por ejemplo, hay un [módulo de idioma cliente npm](https://www.npmjs.com/package/vscode-languageclient) para facilitar la integración de un servidor de idioma en una extensión de VS Code y otro [módulo de lenguaje servidor npm](https://www.npmjs.com/package/vscode-languageserver) para escribir un servidor de idioma mediante Node.js. Se trata de la actual [lista](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) de bibliotecas de compatibilidad.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Mediante el protocolo de servidor de lenguaje en Visual Studio

* [Agregar una extensión de protocolo del servidor idioma](adding-an-lsp-extension.md) -obtener información acerca de cómo integrar un servidor de lenguaje en Visual Studio.
