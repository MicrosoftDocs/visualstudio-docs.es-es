---
title: "Informaci&#243;n r&#225;pida en un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Información rápida, compatibilidad de servicios de lenguaje [managed package framework]"
  - "IntelliSense, información rápida"
  - "Servicios de lenguaje [managed package framework], información rápida de IntelliSense"
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Informaci&#243;n r&#225;pida en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Información rápida de IntelliSense muestra información sobre un identificador en el origen, cuando el usuario ya sea coloca la intercalación en el identificador y selecciona **información rápida** desde el **IntelliSense** menú o mantiene el cursor del mouse sobre el identificador. Esto hace que una información sobre herramientas con información sobre el identificador. Esta información normalmente está formada por el tipo de identificador. Cuando el motor de depuración está activo, esta información puede incluir el valor actual. El motor de depuración proporciona los valores de expresión, mientras que el servicio de lenguaje controla sólo identificadores.  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la nueva forma de implementar las características del servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Tutorial: Mostrar información sobre herramientas de QuickInfo](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md).  
  
> [!NOTE]
>  Se recomienda que comience a utilizar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
 Las clases de servicio de lenguaje de framework \(MPF\) paquete administrados proporcionan compatibilidad completa para mostrar información sobre herramientas información rápida de IntelliSense. Todo lo que debe hacer es proporcionar el texto para mostrar y habilitar la característica información rápida.  
  
 El texto que se mostrará se obtiene llamando el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analizador de método con un valor de la razón de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason>. Ello indica al analizador que obtener la información de tipo \(o lo que sea necesario que se mostrará en la información rápida sobre herramientas\) para el identificador en la ubicación especificada en el <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto. La <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto es lo que se pasó a la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \(método\).  
  
 El analizador debe analizar todo hasta la posición en la <xref:Microsoft.VisualStudio.Package.ParseRequest> objeto con el fin de determinar los tipos de todos los identificadores. A continuación, el analizador debe obtener el identificador en la ubicación de la solicitud de análisis. Por último, el analizador debe pasar los datos de la sugerencia de herramienta asociados con ese identificador para el <xref:Microsoft.VisualStudio.Package.AuthoringScope> de objeto para ese objeto pueda devolver el texto de la <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> \(método\).  
  
## Habilitar la característica información rápida  
 Para habilitar la característica información rápida, debe establecer el `CodeSense` y `QuickInfo` con el nombre de los parámetros de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Estos atributos establecen el <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> y <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> Propiedades.  
  
## Implementación de la característica información rápida  
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> clase controla la operación de información rápida de IntelliSense. Cuando el <xref:Microsoft.VisualStudio.Package.ViewFilter> clase recibe el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando, la clase llama el <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método con la razón para el análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> y la ubicación del símbolo de intercalación en el momento en el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> se envió el comando. El <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analizador de método debe, a continuación, analizar el origen hasta la ubicación especificada y, a continuación, analizar el identificador en la ubicación especificada para determinar qué se debe mostrar en la información rápida sobre herramientas.  
  
 La mayoría de los analizadores hacer un análisis inicial del archivo de código fuente completo y almacenan los resultados en un árbol de análisis. Cuando se realiza el análisis completo <xref:Microsoft.VisualStudio.Package.ParseReason> se pasa a <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \(método\). Otros tipos de análisis, a continuación, pueden utilizar el árbol de análisis para obtener la información deseada.  
  
 Por ejemplo, el valor de razón de análisis de <xref:Microsoft.VisualStudio.Package.ParseReason> puede buscar el identificador en la ubicación de origen y buscar en el árbol de análisis para obtener la información de tipo. Esta información de tipo se pasa a continuación el <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase y devuelve el <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> \(método\).