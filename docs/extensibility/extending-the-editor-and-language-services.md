---
title: Extender el Editor y los servicios de lenguaje | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 4d04f4588b1005e9b5ccb42c6042d01aacb45710
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-editor-and-language-services"></a>Extender el Editor y los servicios de lenguaje
Puede agregar características del servicio de lenguaje (por ejemplo, IntelliSense) a su propio editor y ampliar la mayoría de las características del editor de código de Visual Studio.  Para obtener una lista completa de lo que puede extender, consulte [servicio de lenguaje y los puntos de extensión del Editor de](../extensibility/language-service-and-editor-extension-points.md).  
  
 Amplíe la mayoría características del editor mediante Managed Extensibility Framework (MEF). Por ejemplo, si la característica de editor que desea extender es colores de sintaxis, puede escribir un MEF *componente* que define las clasificaciones que desea diferentes colores y cómo desea que ellos administran. El editor también admite varias extensiones de la misma función.  
  
 La capa de presentación de editor se basa Windows Presentation Framework (WPF). WPF proporciona una biblioteca de gráficos para el formato de texto flexible y proporciona también visualizaciones como gráficos y animaciones.  
  
 El SDK de Visual Studio proporciona adaptadores conocidos como *las correcciones de compatibilidad* para admitir VSPackages escritas para versiones anteriores. Sin embargo, si tienes un VSPackage existente, recomendamos que lo actualice a la nueva tecnología para obtener la confiabilidad y el mejor rendimiento.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Introducción al servicio de lenguaje y extensiones de Editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explica cómo crear una extensión para el editor.|  
|[Dentro del Editor](../extensibility/inside-the-editor.md)|Describe la estructura general del editor y muestra algunas de sus características.|  
|[Managed Extensibility Framework en el Editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explica cómo utilizar Managed Extensibility Framework (MEF) con el editor.|  
|[Servicio de lenguaje y los puntos de extensión del Editor](../extensibility/language-service-and-editor-extension-points.md)|Enumera los puntos de extensión del editor. Puntos de extensión representan las características del editor que se pueden extender.|  
|[Tutorial: Crear un elemento de gráfico de la vista, los comandos y configuración (guías de columnas)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Recorre y explica la creación de un elemento de gráfico de la vista que dibuja líneas gudie de columna para ayudarle a mantener el código para un determinado ancho de pantalla.  También muestra que leer y escribir la configuración, así como declarar y la implementación de comandos que se pueden invocar desde la ventana de comandos.|  
|[Editor de importaciones](../extensibility/editor-imports.md)|Enumera los servicios que puede importar una extensión.|  
|[Adaptar el código heredado en el Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Explica los distintos modos para adaptar el código heredado (previamente Visual Studio 2010) para ampliar el editor.|  
|[Migrar un servicio de lenguaje heredado](../extensibility/internals/migrating-a-legacy-language-service.md)|Explica cómo migrar un servicio de lenguaje en función de VSPackage.|  
|[Tutorial: Vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Muestra cómo vincular un tipo de contenido a una extensión de nombre de archivo.|  
|[Tutorial: Crear un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md)|Muestra cómo agregar un icono a un margen.|  
|[Tutorial: Resaltar texto](../extensibility/walkthrough-highlighting-text.md)|Muestra cómo usar *etiquetas* para resaltar el texto.|  
|[Tutorial: esquematización](../extensibility/walkthrough-outlining.md)|Muestra cómo agregar la esquematización para determinados tipos de llaves.|  
|[Tutorial: Mostrar la coincidencia de llaves](../extensibility/walkthrough-displaying-matching-braces.md)|Muestra cómo resalte de llaves coincidentes.|  
|[Tutorial: Mostrar información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Muestra cómo mostrar elementos emergentes de QuickInfo que describen los elementos de código como propiedades, métodos y eventos.|  
|[Tutorial: Mostrar la Ayuda de firma](../extensibility/walkthrough-displaying-signature-help.md)|Muestra cómo mostrar elementos emergentes que proporcionan información sobre el número y tipos de parámetros en una firma.|  
|[Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)|Muestra cómo implementar la finalización de instrucciones.|  
|[Tutorial: Implementar fragmentos de código](../extensibility/walkthrough-implementing-code-snippets.md)|Muestra cómo implementar la expansión de fragmento de código.|  
|[Tutorial: Mostrar sugerencias de bombilla](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Muestra cómo mostrar las bombillas para obtener sugerencias de código.|  
|[Tutorial: Usar un comando de Shell con una extensión del Editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Muestra cómo asociar un comando de menú en un VSPackage un componente MEF.|  
|[Tutorial: Usar una tecla de método abreviado con una extensión del Editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Muestra cómo asociar un menú contextual en un VSPackage un componente MEF.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Proporciona información acerca de Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Proporciona información acerca de Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Referencia  
 El editor de Visual Studio incluye los siguientes espacios de nombres.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense></xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification></xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor></xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text></xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments></xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification></xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing></xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document></xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor></xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods></xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting></xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch></xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations></xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining></xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection></xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging></xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities></xref:Microsoft.VisualStudio.Utilities>
