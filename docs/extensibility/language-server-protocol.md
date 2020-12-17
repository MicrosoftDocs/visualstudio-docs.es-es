---
title: Información general del protocolo del servidor de idioma | Microsoft Docs
description: Obtenga información acerca de cómo el protocolo del servidor de lenguaje proporciona un marco útil para exponer las características del lenguaje a una variedad de herramientas.
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 6a7d93c2-31ea-4bae-8b29-6988a567ddf2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d642d1168cbd2a8bd7abadbcdbd7c1e2851b00e
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616135"
---
# <a name="language-server-protocol"></a>Protocolo de servidor de lenguaje

## <a name="what-is-the-language-server-protocol"></a>¿Qué es el protocolo de servidor de lenguaje?

La compatibilidad con características de edición enriquecidas como la finalización automática del código fuente o **ir a definición** para un lenguaje de programación en un editor o IDE es tradicionalmente muy desafiante y lento. Normalmente, es necesario escribir un modelo de dominio (un escáner, un analizador, un comprobador de tipos, un generador, etc.) en el lenguaje de programación del editor o el IDE. Por ejemplo, el complemento de CDT de Eclipse, que proporciona compatibilidad con C/C++ en el IDE de Eclipse, está escrito en Java, ya que el propio IDE de Eclipse está escrito en Java. Siguiendo este enfoque, significaría implementar un modelo de dominio de C/C++ en TypeScript para Visual Studio código y un modelo de dominio independiente en C# para Visual Studio.

Crear modelos de dominio específicos del lenguaje también es mucho más sencillo si una herramienta de desarrollo puede volver a usar bibliotecas específicas del lenguaje existentes. Sin embargo, estas bibliotecas se implementan normalmente en el propio lenguaje de programación (por ejemplo, los buenos modelos de dominio de C/C++ se implementan en C/C++). La integración de una biblioteca de C/C++ en un editor escrito en TypeScript es técnicamente posible pero difícil de hacer.

### <a name="language-servers"></a>Servidores de idioma

Otro enfoque consiste en ejecutar la biblioteca en su propio proceso y usar la comunicación entre procesos para comunicarse con ella. Los mensajes que se envían de un modo a otro, forman un protocolo. El protocolo de servidor de lenguaje (LSP) es el producto de estandarizar los mensajes intercambiados entre una herramienta de desarrollo y un proceso de servidor de lenguaje. El uso de servidores de idioma o Demons no es una idea nueva o novedosa. Los editores como vim y Emacs han hecho esto durante algún tiempo para proporcionar compatibilidad con la finalización automática semántica. El objetivo del LSP era simplificar este tipo de integraciones y proporcionar un marco útil para exponer las características del lenguaje a una variedad de herramientas.

Tener un protocolo común permite la integración de las características del lenguaje de programación en una herramienta de desarrollo con un uso mínimo mediante la reutilización de una implementación existente del modelo de dominio del lenguaje. Un back-end de servidor de idioma se podría escribir en PHP, Python o Java y el LSP permite integrarlo fácilmente en una gran variedad de herramientas. El protocolo funciona en un nivel común de abstracción para que una herramienta pueda ofrecer servicios de lenguaje enriquecidos sin necesidad de comprender totalmente los matices específicos del modelo de dominio subyacente.

## <a name="how-work-on-the-lsp-started"></a>Cómo se inició el trabajo en el LSP

El LSP ha evolucionado a lo largo del tiempo y hoy tiene la versión 3,0. Se inició cuando OmniSharp tomó el concepto de un servidor de lenguaje para proporcionar características de edición enriquecidas para C#. Inicialmente, OmniSharp usaba el protocolo HTTP con una carga de JSON y se integró en varios editores, como [Visual Studio Code](https://code.visualstudio.com).

Aproximadamente al mismo tiempo, Microsoft empezó a trabajar en un servidor de lenguaje TypeScript, con la idea de admitir TypeScript en editores como Emacs y Sublime Text. En esta implementación, un editor se comunica a través de stdin/stdout con el proceso del servidor TypeScript y usa una carga JSON inspirado por el protocolo del depurador de la V8 para solicitudes y respuestas. El servidor TypeScript se ha integrado en el complemento de sublime de TypeScript y VS Code para la edición de TypeScript enriquecida.

Después de haber integrado dos servidores de idioma diferentes, el equipo de VS Code comenzó a explorar un protocolo de Common Language Server para editores e IDE. Un protocolo común permite a un proveedor de lenguaje crear un servidor de un solo idioma que pueden consumir distintos IDE. Un consumidor de servidor de lenguaje solo tiene que implementar una vez el lado cliente del protocolo. Esto da como resultado una situación Win-Win tanto para el proveedor de lenguaje como para el consumidor de lenguaje.

El protocolo de servidor de lenguaje se ha iniciado con el protocolo usado por el servidor TypeScript y lo expande con más características de lenguaje inspirados en la API de VS Code Language. El protocolo está respaldado por JSON-RPC para la invocación remota debido a su simplicidad y bibliotecas existentes.

El equipo de VS Code ha prototipodo el protocolo mediante la implementación de varios servidores de idioma de pelusa que responden a las solicitudes a pelusa (Scan) de un archivo y devuelven un conjunto de advertencias y errores detectados. El objetivo era deshacer la desactivación de un archivo cuando el usuario edita un documento, lo que significa que habrá muchas solicitudes de detección de errores durante una sesión del editor. Tenía sentido mantener un servidor activo y en funcionamiento para que no sea necesario iniciar un nuevo proceso de detección de errores para cada edición del usuario. Se han implementado varios servidores de pelusa, incluidas las extensiones ESLint y TSLint de VS Code. Estos dos servidores de pelusa se implementan en TypeScript/JavaScript y se ejecutan en Node.js. Comparten una biblioteca que implementa la parte del cliente y del servidor del protocolo.

## <a name="how-the-lsp-works"></a>Cómo funciona el LSP

Un servidor de lenguaje se ejecuta en su propio proceso y herramientas como Visual Studio o VS Code comunicarse con el servidor mediante el protocolo de lenguaje a través de JSON-RPC. Otra ventaja del servidor de lenguaje que funciona en un proceso dedicado es que se evitan los problemas de rendimiento relacionados con un solo modelo de proceso. El canal de transporte real puede ser stdio, sockets, canalizaciones con nombre o IPC de nodo si el cliente y el servidor están escritos en Node.js.

A continuación se muestra un ejemplo de cómo una herramienta y un servidor de idioma se comunican durante una sesión de edición rutinaria:

![diagrama de flujo de LSP](media/lsp-flow-diagram.png)

* **El usuario abre un archivo (denominado documento) en la herramienta**: la herramienta notifica al servidor de idioma que un documento está abierto (' TextDocument/didOpen '). A partir de ahora, la verdad sobre el contenido del documento ya no se encuentra en el sistema de archivos, pero la herramienta se mantiene en la memoria.

* **El usuario realiza modificaciones**: la herramienta notifica al servidor sobre el cambio del documento (' TextDocument/didChange ') y el servidor de idioma actualiza la información semántica del programa. Como ocurre, el servidor de lenguaje analiza esta información y notifica a la herramienta los errores y advertencias detectados (' textDocument/publishDiagnostics ').

* **El usuario ejecuta "ir a definición" en un símbolo en el editor**: la herramienta envía una solicitud ' textDocument/Definition ' con dos parámetros: (1) el URI del documento y (2) la posición del texto desde donde se inició la solicitud ir a definición en el servidor. El servidor responde con el URI del documento y la posición de la definición del símbolo dentro del documento.

* **El usuario cierra el documento (archivo)**: se envía una notificación ' TextDocument/didClose ' desde la herramienta, que informa al servidor de idioma de que el documento ya no está en memoria y que el contenido actual está ahora actualizado en el sistema de archivos.

En este ejemplo se muestra cómo el protocolo se comunica con el servidor de lenguaje en el nivel de características del editor como "ir a definición", "Buscar todas las referencias". Los tipos de datos que usa el protocolo son el editor o los tipos de datos del IDE, como el documento de texto abierto actualmente y la posición del cursor. Los tipos de datos no se encuentran en el nivel de un modelo de dominio de lenguaje de programación que normalmente proporcionaría árboles de sintaxis abstracta y símbolos de compilador (por ejemplo, tipos resueltos, espacios de nombres, etc.). Esto simplifica significativamente el protocolo.

Ahora veamos la solicitud ' textDocument/Definition ' con más detalle. A continuación se muestran las cargas que van entre la herramienta cliente y el servidor de idioma para la solicitud "ir a definición" en un documento de C++.

Esta es la solicitud:

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

En Retrospect, la descripción de los tipos de datos en el nivel del editor en lugar de en el nivel del modelo de lenguaje de programación es uno de los motivos por los que el protocolo del servidor de lenguaje se ha realizado correctamente. Es mucho más sencillo normalizar un URI de documento de texto o una posición del cursor en comparación con la estandarización de un árbol de sintaxis abstracta y símbolos del compilador en diferentes lenguajes de programación.

Cuando un usuario trabaja con distintos idiomas, VS Code suele iniciar un servidor de idioma para cada lenguaje de programación. En el ejemplo siguiente se muestra una sesión en la que el usuario trabaja en archivos Java y SASS.

![Java y Sass](media/lsp-java-and-sass.png)

### <a name="capabilities"></a>Funcionalidades

No todos los servidores de idioma admiten todas las características definidas por el protocolo. Por lo tanto, el cliente y el servidor anuncian su conjunto de características compatible a través de ' Capabilities '. Por ejemplo, un servidor anuncia que puede controlar la solicitud ' textDocument/Definition ', pero puede que no controle la solicitud ' Workspace/Symbol '. De forma similar, los clientes pueden anunciar que pueden proporcionar notificaciones "a punto de guardar" antes de guardar un documento, de modo que un servidor pueda calcular ediciones textuales para dar formato al documento editado automáticamente.

## <a name="integrating-a-language-server"></a>Integración de un servidor de idioma

La integración real de un servidor de idioma en una herramienta concreta no está definida por el protocolo del servidor de lenguaje y se deja a los implementadores de la herramienta. Algunas herramientas integran los servidores de idioma de forma genérica al tener una extensión que puede iniciarse y comunicarse con cualquier tipo de servidor de lenguaje. Otros, como VS Code, crean una extensión personalizada por servidor de idioma, por lo que una extensión sigue pudiendo proporcionar algunas características de lenguaje personalizado.

Para simplificar la implementación de servidores de idioma y clientes, hay bibliotecas o SDK para las partes de cliente y servidor. Estas bibliotecas se proporcionan para distintos idiomas. Por ejemplo, hay un [módulo NPM Client de Language](https://www.npmjs.com/package/vscode-languageclient) para facilitar la integración de un servidor de idioma en una extensión de vs Code y otro [módulo NPM del servidor de idioma](https://www.npmjs.com/package/vscode-languageserver) para escribir un servidor de idioma mediante Node.js. Esta es la [lista](https://github.com/Microsoft/language-server-protocol/wiki/Protocol-Implementations) actual de bibliotecas de soporte técnico.

## <a name="using-the-language-server-protocol-in-visual-studio"></a>Usar el protocolo de servidor de lenguaje en Visual Studio

* [Agregar una extensión de protocolo del servidor de lenguaje](adding-an-lsp-extension.md) : Obtenga información sobre cómo integrar un servidor de idioma en Visual Studio.
