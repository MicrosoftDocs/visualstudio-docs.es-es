---
title: Personalizar la transformación de texto T4
description: Obtenga información sobre cómo puede ampliar el proceso de transformación de plantilla predeterminado personalizando el procesador de directivas de plantilla de texto o el host de plantilla de texto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 35942b5f87458d1ccaf4892d33b5bba1dcdbb8a0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389363"
---
# <a name="customize-t4-text-transformation"></a>Personalizar la transformación de texto T4

Las plantillas de texto son una característica de Visual Studio que le permiten generar código de programa u otros archivos de texto a través de un proceso de transformación. Con , puede extender el proceso de transformación de plantilla predeterminado personalizando el procesador de directivas de plantilla de [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] texto o el host de plantilla de texto.

## <a name="in-this-section"></a>En esta sección

 [El proceso de transformación Plantilla de texto](../modeling/the-text-template-transformation-process.md) Describe cómo funciona la transformación de texto y explica el rol del host de plantilla y los procesadores de directivas.

 [Creación de procesadores de directivas de plantillas de texto T4 personalizados](../modeling/creating-custom-t4-text-template-directive-processors.md) El procesador de directivas se ocupa de las directivas de la plantilla, como Se ejecuta durante la compilación de la plantilla y puede cargar ensamblados `<#@template#>.` y otros recursos. También puede insertar código que cargará recursos en tiempo de ejecución. Al definir su propio procesador de directivas, puede reducir la complejidad de las plantillas.

 [Invocación de la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md) Si va a escribir una extensión Visual Studio, como un comando de menú o un controlador de eventos, la extensión puede usar el Servicio de plantillas de texto para transformar cualquier plantilla de texto. Puede pasar datos de parámetros a la plantilla mediante el objeto Session y obtener los valores desde dentro de la plantilla mediante la `<#@parameter#>` directiva .

 [Procesamiento de plantillas de texto mediante un host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md) Cuando se ejecuta el código de la plantilla de texto, el host proporciona acceso a archivos externos y al estado de la aplicación. Por ejemplo, el host que ejecuta transformaciones de texto en Visual Studio puede proporcionar acceso a **Explorador de soluciones**. También muestra errores en la ventana del mensaje de error. Si desea ejecutar transformaciones de texto en un contexto diferente, puede definir su propio host que proporciona acceso a los servicios disponibles en ese contexto.

 Si está escribiendo una extensión Visual Studio, considere la posibilidad de usar el servicio de transformación de texto existente en lugar de escribir su propio host. Para obtener más información, vea [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Referencia

- [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md) proporciona la sintaxis de directivas de plantilla de texto y bloques de control.
