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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ea2881cfebaf10d7a72e8651214cf3a6f64debae
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996279"
---
# <a name="customizing-t4-text-transformation"></a>Personalizar la transformación de texto T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las plantillas de texto son una característica de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que permiten generar código de programa u otros archivos de texto a través de un proceso de transformación. Uso de [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)], puede extender el proceso de transformación de plantilla predeterminado personalizando el procesador de directivas de plantilla de texto o el host de plantilla de texto.  
  
## <a name="in-this-section"></a>En esta sección  
 [El proceso de transformación de las plantillas de texto](../modeling/the-text-template-transformation-process.md)  
 Describe cómo funciona la transformación de texto y se explica el rol de host de la plantilla y los procesadores de directivas.  
  
 [Crear procesadores de directivas personalizadas para las plantillas de texto T4](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 El procesador de directivas se ocupa de las directivas en la plantilla, como `<#@template#>.` se ejecuta durante la compilación de la plantilla y puede cargar ensamblados y otros recursos. También puede insertar código que carga los recursos en tiempo de ejecución. Al definir su propio procesador de directivas, puede reducir la complejidad de las plantillas.  
  
 [Invocar la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Si está escribiendo un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensión como un controlador de comando o evento de menú, la extensión puede usar el servicio de plantillas de texto para transformar cualquier plantilla de texto. Puede pasar datos del parámetro en la plantilla mediante el objeto de sesión y obtener los valores desde dentro de la plantilla mediante el `<#@parameter#>` directiva.  
  
 [Procesar las plantillas de texto mediante un host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Cuando se ejecuta el código de la plantilla de texto, el host proporciona acceso a archivos externos y el estado de la aplicación. Por ejemplo, el host que ejecuta las transformaciones de texto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] puede proporcionar acceso al explorador de soluciones. También muestra los errores en la ventana de mensaje de error. Si desea ejecutar transformaciones de texto en un contexto diferente, puede definir su propio host que proporciona acceso a los servicios disponibles en ese contexto.  
  
 Si está escribiendo un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensión, considere la posibilidad de utilizar el servicio de transformación de texto existente en lugar de escribir su propio host. Para obtener más información, consulte [invocar la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Referencia  
 [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)  
  
 Proporciona la sintaxis de directivas de plantilla de texto y bloques de control.
