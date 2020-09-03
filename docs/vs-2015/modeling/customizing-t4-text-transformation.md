---
title: Personalizar la transformación de texto T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 71cec79acfcc934f9ddd910006f32f5207b26c84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654964"
---
# <a name="customizing-t4-text-transformation"></a>Personalizar la transformación de texto T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las plantillas de texto son una característica de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que le permite generar código de programa u otros archivos de texto a través de un proceso de transformación. Con [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)] , puede extender el proceso de transformación de plantillas predeterminado personalizando el procesador de directivas de plantillas de texto o el host de plantilla de texto.

## <a name="in-this-section"></a>En esta sección
 [El proceso de transformación de plantillas de texto](../modeling/the-text-template-transformation-process.md) Describe cómo funciona la transformación de texto y explica el rol del host de plantilla y los procesadores de directivas.

 [Crear procesadores de directivas de plantillas de texto T4 personalizadas](../modeling/creating-custom-t4-text-template-directive-processors.md) El procesador de directivas trata las directivas de la plantilla, como se `<#@template#>.` ejecuta durante la compilación de la plantilla, y puede cargar ensamblados y otros recursos. También puede insertar código que cargará los recursos en tiempo de ejecución. Al definir su propio procesador de directivas, puede reducir la complejidad de las plantillas.

 [Invocar la transformación de texto en una extensión de vs](../modeling/invoking-text-transformation-in-a-vs-extension.md) Si está escribiendo una extensión, como [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] un comando de menú o un controlador de eventos, la extensión puede utilizar el servicio de plantillas de texto para transformar cualquier plantilla de texto. Puede pasar datos de parámetros a la plantilla mediante el objeto de sesión y obtener los valores de dentro de la plantilla mediante la `<#@parameter#>` Directiva.

 [Procesamiento de plantillas de texto mediante un host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md) Cuando se ejecuta el código de la plantilla de texto, el host proporciona acceso a los archivos externos y al estado de la aplicación. Por ejemplo, el host que ejecuta las transformaciones de texto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] puede proporcionar acceso al explorador de soluciones. También se muestran errores en la ventana de mensajes de error. Si desea ejecutar transformaciones de texto en un contexto diferente, puede definir su propio host que proporciona acceso a los servicios disponibles en ese contexto.

 Si está escribiendo una [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensión, considere la posibilidad de usar el servicio de transformación de texto existente en lugar de escribir su propio host. Para obtener más información, consulte [invocar la transformación de texto en una extensión de vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Referencia
 [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)

 Proporciona la sintaxis de las directivas de plantilla de texto y los bloques de control.
