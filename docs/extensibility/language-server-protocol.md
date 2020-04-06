---
title: Descripción general del protocolo de servidor de idiomas ( Language Server Protocol Overview ) Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3bd5dce3cfb7022a8abb6397dc87b418144cbe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703100"
---
# <a name="language-server-protocol"></a>Protocolo de servidor de lenguaje

## <a name="what-is-the-language-server-protocol"></a>¿Qué es el protocolo de servidor de idioma?

La compatibilidad con funciones de edición enriquecidas como las autocompletars de código fuente o **Ir a definición** para un lenguaje de programación en un editor o IDE es tradicionalmente muy difícil y consume mucho tiempo. Normalmente requiere escribir un modelo de dominio (un analizador, un analizador, un comprobador de tipos, un generador y más) en el lenguaje de programación del editor o IDE. Por ejemplo, el plugin CDT de Eclipse, que proporciona soporte para C/C++ en el IDE de Eclipse, está escrito en Java ya que el IDE de Eclipse está escrito en Java. Siguiendo este enfoque, significaría implementar un modelo de dominio de C/C++ en TypeScript para Visual Studio Code y un modelo de dominio independiente en C- para Visual Studio.

La creación de modelos de dominio específicos del lenguaje también es mucho más fácil si una herramienta de desarrollo puede reutilizar bibliotecas específicas del lenguaje existentes. Sin embargo, estas bibliotecas se implementan normalmente en el propio lenguaje de programación (por ejemplo, se implementan buenos modelos de dominio C/C++en C/C++). Integrar una biblioteca C/C++ en un editor escrito en TypeScript es técnicamente posible pero difícil de hacer.

### <a name="language-servers"></a>Servidores de idiomas

Otro enfoque es ejecutar la biblioteca en su propio proceso y utilizar la comunicación entre procesos para hablar con ella. Los mensajes enviados de ida y vuelta forman un protocolo. El protocolo de servidor de lenguaje (LSP) es el producto de estandarizar los mensajes intercambiados entre una herramienta de desarrollo y un proceso de servidor de lenguaje. El uso de servidores de lenguaje o demonios no es una idea nueva o novedosa. Editores como Vim y Emacs han estado haciendo esto durante algún tiempo para proporcionar soporte de autocompletado semántico. El objetivo del LSP era simplificar este tipo de integraciones y proporcionar un marco útil para exponer las características del lenguaje a una variedad de herramientas.

Tener un protocolo común permite la integración de características del lenguaje de programación en una herramienta de desarrollo con un mínimo alboroto mediante la reutilización de una implementación existente del modelo de dominio del lenguaje. Un back-end de servidor de lenguaje podría escribirse en PHP, Python o Java y el LSP permite integrarlo fácilmente en una variedad de herramientas. El protocolo funciona en un nivel común de abstracción para que una herramienta pueda ofrecer servicios de lenguaje enriquecido sin necesidad de comprender completamente los matices específicos del modelo de dominio subyacente.

## <a name="how-work-on-the-lsp-started"></a>Cómo comenzó el trabajo en el LSP

El LSP ha evolucionado con el tiempo y hoy está en la versión 3.0. Se inició cuando OmniSharp recogió el concepto de un servidor de lenguaje para proporcionar funciones de edición enriquecidas para C. Inicialmente, OmniSharp utilizaba el protocolo HTTP con una carga JSON y se ha integrado en varios editores, incluido [Visual Studio Code](https://code.visualstudio.com).

Al mismo tiempo, Microsoft comenzó a trabajar en un servidor de lenguaje TypeScript, con la idea de admitir TypeScript en editores como Emacs y Sublime Text. En esta implementación, un editor se comunica a través de stdin/stdout con el proceso de servidor TypeScript y utiliza una carga JSON inspirada en el protocolo de depurador V8 para solicitudes y respuestas. El servidor TypeScript se ha integrado en el plugin TypeScript Sublime y VS Code para la edición de TypeScript enriquecida.

Después de haber integrado dos servidores de lenguaje diferentes, el equipo de VS Code comenzó a explorar un protocolo de servidor de lenguaje común para editores e IDE. Un protocolo común permite a un proveedor de lenguaje crear un único servidor de idioma que pueden ser consumidos por diferentes IDE. Un consumidor de servidor de lenguaje solo tiene que implementar el lado cliente del protocolo una vez. Esto da como resultado una situación de ganar-ganar tanto para el proveedor de idioma como para el consumidor de idiomas.

El protocolo de servidor de lenguaje se inició con el protocolo utilizado por el servidor TypeScript, expandiéndolo con más características de lenguaje inspiradas en la API de lenguaje de VS Code. El protocolo está respaldado por JSON-RPC para la invocación remota debido a su simplicidad y bibliotecas existentes.

El equipo de VS Code creó el prototipo del protocolo mediante la implementación de varios servidores de lenguaje linter que responden a las solicitudes de pelusa (escanear) un archivo y devolver un conjunto de advertencias y errores detectados. El objetivo era pelar un archivo a medida que el usuario edita en un documento, lo que significa que habrá muchas solicitudes de linting durante una sesión de editor. Tenía sentido mantener un servidor en funcionamiento para que no era necesario iniciar un nuevo proceso de linting para cada edición de usuario. Se implementaron varios servidores linter, incluidas las extensiones ESLint y TSLint de VS Code. Estos dos servidores linter se implementan en TypeScript/JavaScript y se ejecutan en Node.js. Comparten una biblioteca que implementa la parte de cliente y servidor del protocolo.

## <a name="how-the-lsp-works"></a>Cómo funciona el LSP

Un servidor de lenguaje se ejecuta en su propio proceso y herramientas como Visual Studio o VS Code se comunican con el servidor mediante el protocolo de lenguaje a través de JSON-RPC. Otra ventaja del servidor de lenguaje que funciona en un proceso dedicado es que se evitan los problemas de rendimiento relacionados con un único modelo de proceso. El canal de transporte real puede ser stdio, sockets, canalizaciones con nombre o ipc de nodo si tanto el cliente como el servidor están escritos en Node.js.

A continuación se muestra un ejemplo de cómo una herramienta y un servidor de lenguaje se comunican durante una sesión de edición de rutina:

![diagrama de flujo lsp](media/lsp-flow-diagram.png)

* **El usuario abre un archivo (denominado documento) en la herramienta**: La herramienta notifica al servidor de idioma que un documento está abierto ('textDocument/didOpen'). A partir de ahora, la verdad sobre el contenido del documento ya no está en el sistema de archivos, sino que la herramienta lo guarda en la memoria.

* **El usuario realiza modificaciones**: La herramienta notifica al servidor sobre el cambio de documento ('textDocument/didChange') y la información semántica del programa es actualizada por el servidor de lenguaje. A medida que esto sucede, el servidor de lenguaje analiza esta información y notifica a la herramienta con los errores y advertencias detectados ('textDocument/publishDiagnostics').

* **El usuario ejecuta "Ir a definición" en un símbolo en el editor:** La herramienta envía una solicitud 'textDocument/definition' con dos parámetros: (1) el URI del documento y (2) la posición de texto desde donde se inició la solicitud Ir a definición al servidor. El servidor responde con el URI del documento y la posición de la definición del símbolo dentro del documento.

* **El usuario cierra el documento (archivo):** se envía una notificación 'textDocument/didClose' desde la herramienta, informando al servidor de lenguaje que el documento ya no está en la memoria y que el contenido actual está ahora actualizado en el sistema de archivos.

Este ejemplo ilustra cómo el protocolo se comunica con el servidor de lenguaje en el nivel de características del editor como "Ir a definición", "Buscar todas las referencias". Los tipos de datos utilizados por el protocolo son editor o IDE 'tipos de datos' como el documento de texto abierto actualmente y la posición del cursor. Los tipos de datos no están en el nivel de un modelo de dominio de lenguaje de programación que normalmente proporcionaría árboles de sintaxis abstracta y símbolos del compilador (por ejemplo, tipos resueltos, espacios de nombres, ...). Esto simplifica significativamente el protocolo.

Ahora echemos un vistazo a la solicitud 'textDocument/definition' con más detalle. A continuación se muestran las cargas útiles que van entre la herramienta cliente y el servidor de idioma para la solicitud "Ir a definición" en un documento C++.

Esta es la petición:

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

Esta es la respuesta:

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

En retrospectiva, describir los tipos de datos en el nivel del editor en lugar de en el nivel del modelo de lenguaje de programación es una de las razones del éxito del protocolo de servidor de lenguaje. Es mucho más sencillo estandarizar un URI de documento de texto o una posición de cursor en comparación con la estandarización de un árbol de sintaxis abstracta y símbolos del compilador en diferentes lenguajes de programación.

Cuando un usuario está trabajando con diferentes idiomas, VS Code normalmente inicia un servidor de lenguaje para cada lenguaje de programación. El ejemplo siguiente muestra una sesión donde el usuario trabaja en archivos Java y SASS.

![java y sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Capacidades

No todos los servidores de lenguaje pueden admitir todas las características definidas por el protocolo. Por lo tanto, el cliente y el servidor anuncian su conjunto de características compatibles a través de 'capacidades'. Por ejemplo, un servidor anuncia que puede controlar la solicitud 'textDocument/definition', pero es posible que no controle la solicitud 'workspace/symbol'. Del mismo modo, los clientes pueden anunciar que pueden proporcionar notificaciones de "a punto de guardar" antes de guardar un documento, de modo que un servidor pueda calcular las ediciones textuales para dar formato automáticamente al documento editado.

## <a name="integrating-a-language-server"></a>Integración de un servidor de idiomas

La integración real de un servidor de lenguaje en una herramienta determinada no está definida por el protocolo de servidor de lenguaje y se deja a los implementadores de la herramienta. Algunas herramientas integran servidores de lenguaje de forma genérica al tener una extensión que puede iniciar y hablar con cualquier tipo de servidor de lenguaje. Otros, como VS Code, crean una extensión personalizada por servidor de lenguaje, de modo que una extensión todavía pueda proporcionar algunas características de lenguaje personalizado.

Para simplificar la implementación de clientes y servidores de lenguaje, hay bibliotecas o SDK para las partes de cliente y servidor. Estas bibliotecas se proporcionan para diferentes idiomas. Por ejemplo, hay un [módulo npm](https://www.npmjs.com/package/vscode-languageclient) de cliente de lenguaje para facilitar la integración de un servidor de lenguaje en una extensión de código VS y otro [módulo npm](https://www.npmjs.com/package/vscode-languageserver) de servidor de idioma para escribir un servidor de lenguaje mediante Node.js. Esta es la [lista](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) actual de bibliotecas de soporte.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Uso del protocolo de servidor de lenguaje en Visual Studio

* [Agregar una extensión](adding-an-lsp-extension.md) de protocolo de servidor de lenguaje: obtenga información sobre cómo integrar un servidor de lenguaje en Visual Studio.
