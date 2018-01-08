---
title: "Personalizar la transformación de texto T4 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: "28"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 98d7efc90a07de02f255afe1a75d10fef749e88a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-t4-text-transformation"></a>Personalizar la transformación de texto T4
Plantillas de texto son una característica de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que le permiten generar código de programa u otros archivos de texto a través de un proceso de transformación. Usar [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], puede extender el proceso de transformación de plantillas predeterminado personalizando el procesador de directivas de plantilla de texto o el host de plantillas de texto.  
  
## <a name="in-this-section"></a>En esta sección  
 [El proceso de transformación de las plantillas de texto](../modeling/the-text-template-transformation-process.md)  
 Describe cómo funciona la transformación de texto y se explica el rol del host de plantilla y los procesadores de directivas.  
  
 [Crear procesadores de directivas personalizadas para las plantillas de texto T4](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 El procesador de directivas se ocupa de las directivas de la plantilla, como `<#@template#>.` se ejecuta durante la compilación de la plantilla y puede cargar ensamblados y otros recursos. También puede insertar código que cargará los recursos en tiempo de ejecución. Al definir su propio procesador de directivas, puede reducir la complejidad de las plantillas.  
  
 [Invocar la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Si está escribiendo un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensión como un controlador de eventos o de comando de menú, la extensión puede utilizar el servicio de plantillas de texto para transformar una plantilla de texto. Puede pasar datos del parámetro en la plantilla mediante el objeto de sesión y obtener los valores desde dentro de la plantilla mediante el `<#@parameter#>` directiva.  
  
 [Procesar las plantillas de texto mediante un host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Cuando se ejecuta el código de la plantilla de texto, el host proporciona acceso a archivos externos y el estado de la aplicación. Por ejemplo, el host que ejecuta las transformaciones de texto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede proporcionar acceso al explorador de soluciones. También muestra los errores en la ventana de mensaje de error. Si desea ejecutar transformaciones de texto en un contexto diferente, puede definir su propio host que proporciona acceso a los servicios disponibles en ese contexto.  
  
 Si está escribiendo un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensión, considere la posibilidad de utilizar el servicio de transformación de texto existente en lugar de escribir su propio host. Para obtener más información, consulte [invocar la transformación de texto en una extensión de VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Referencia  
 [Escribir una plantilla de texto T4](../modeling/writing-a-t4-text-template.md)  
  
 Proporciona la sintaxis de directivas de plantilla de texto y bloques de control.