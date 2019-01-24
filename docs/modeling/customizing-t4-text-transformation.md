---
title: Personalizar la transformación de texto T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: f88e7dbd95d62a17c048bf5fb01785799c3a6ce0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845725"
---
# <a name="customize-t4-text-transformation"></a>Personalizar la transformación de texto T4

Las plantillas de texto son una característica de Visual Studio que permiten generar código de programa u otros archivos de texto a través de un proceso de transformación. Uso de [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], puede extender el proceso de transformación de plantilla predeterminado personalizando el procesador de directivas de plantilla de texto o el host de plantilla de texto.

## <a name="in-this-section"></a>En esta sección

 [El proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md) describe cómo funciona la transformación de texto y se explica el rol de host de la plantilla y los procesadores de directivas.

 [Crear procesadores de directiva de plantilla de texto personalizado T4](../modeling/creating-custom-t4-text-template-directive-processors.md) el procesador de directivas se ocupa de las directivas en la plantilla, como `<#@template#>.` se ejecuta durante la compilación de la plantilla y puede cargar ensamblados y otros recursos. También puede insertar código que carga los recursos en tiempo de ejecución. Al definir su propio procesador de directivas, puede reducir la complejidad de las plantillas.

 [Invocar la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md) si está escribiendo una extensión de Visual Studio como un controlador de comando o evento de menú, la extensión puede usar el servicio de plantillas de texto para transformar cualquier plantilla de texto. Puede pasar datos del parámetro en la plantilla mediante el objeto de sesión y obtener los valores desde dentro de la plantilla mediante el `<#@parameter#>` directiva.

 [Procesar las plantillas de texto mediante un Host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md) cuando se ejecuta el código de la plantilla de texto, el host proporciona acceso a archivos externos y el estado de la aplicación. Por ejemplo, el host que ejecuta las transformaciones de texto en Visual Studio puede proporcionar acceso a **el Explorador de soluciones**. También muestra los errores en la ventana de mensaje de error. Si desea ejecutar transformaciones de texto en un contexto diferente, puede definir su propio host que proporciona acceso a los servicios disponibles en ese contexto.

 Si está escribiendo una extensión de Visual Studio, considere la posibilidad de utilizar el servicio de transformación de texto existente en lugar de escribir su propio host. Para obtener más información, consulte [invocar la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Referencia

- [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md) proporciona la sintaxis de directivas de plantilla de texto y bloques de control.