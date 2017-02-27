---
title: "Customizing T4 Text Transformation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, API"
  - "text templates, custom hosts"
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 28
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 28
---
# Customizing T4 Text Transformation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las plantillas de texto son una característica de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que permite generar código de programa u otros archivos de texto a través de un proceso de transformación.  Con [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], puede extender el proceso de transformación de plantillas predeterminado personalizando el procesador de directivas de plantilla de texto o el host de plantillas de texto.  
  
## En esta sección  
 [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md)  
 Describe cómo funciona la transformación de texto y explica el rol del host de plantilla y de los procesadores de directivas.  
  
 [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 El procesador de directivas trabaja con las directivas de la plantilla, como `<#@template#>.` Se ejecuta durante la compilación de la plantilla, y puede cargar ensamblados y otros recursos.  También puede insertar código que cargará recursos en tiempo de ejecución.  Si define su propio procesador de directivas, puede reducir la complejidad de las plantillas.  
  
 [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Si está escribiendo una extensión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como un comando de menú o controlador de eventos, la extensión puede utilizar el servicio de plantillas de texto para transformar cualquier plantilla de texto.  Puede pasar los datos de parámetro en la plantilla mediante el objeto Session y obtener los valores desde dentro la plantilla utilizando la directiva `<#@parameter#>`.  
  
 [Processing Text Templates by using a Custom Host](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Cuando el código de la plantilla de texto se ejecuta, el host proporciona acceso a los archivos externos y el estado de la aplicación.  Por ejemplo, el host que ejecuta las transformaciones de texto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede proporcionar acceso a un explorador de soluciones.  También muestra los errores en la ventana de mensajes de error.  Si desea ejecutar transformaciones de texto en un contexto diferente, puede definir su propio host que proporcione acceso a los servicios disponibles en ese contexto.  
  
 Si está escribiendo una extensión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], considere la posibilidad de utilizar el servicio transformación de texto en lugar de escribir su propio host.  Para obtener más información, vea [Invoking Text Transformation in a VS Extension](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## Referencia  
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)  
  
 Proporciona la sintaxis de las directivas y los bloques de control de plantilla de texto.