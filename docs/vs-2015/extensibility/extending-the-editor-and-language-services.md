---
title: Ampliación del Editor y los servicios de lenguaje | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8102b8fb4afc02ca0540d75b3c0d08ef75b964d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579288"
---
# <a name="extending-the-editor-and-language-services"></a>Ampliación del editor y los servicios de lenguaje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ampliación del Editor y los servicios de lenguaje](https://docs.microsoft.com/visualstudio/extensibility/extending-the-editor-and-language-services).  
  
Puede agregar características del servicio de lenguaje (por ejemplo, IntelliSense) a su propio editor y ampliar la mayoría de las características del editor de código de Visual Studio.  Para obtener una lista completa de lo que puede extender, consulte [servicio de lenguaje y puntos de extensión del Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
 Extender la mayoría de las características de editor mediante el uso de Managed Extensibility Framework (MEF). Por ejemplo, si desea extender la característica del editor es el color de sintaxis, puede escribir un MEF *parte componente* que define las clasificaciones que quiere distintos colores y cómo desea que ellos administran. El editor también admite varias extensiones de la misma característica.  
  
 La capa de presentación del editor se basa Windows Presentation Framework (WPF). WPF proporciona una biblioteca de gráficos para dar formato al texto flexible y también proporciona visualizaciones como gráficos y animaciones.  
  
 El SDK de Visual Studio permite a los adaptadores que se conoce como *las correcciones de compatibilidad* para admitir los VSPackages escritos para versiones anteriores. No obstante, si tiene un VSPackage existente, se recomienda actualizarlo a la nueva tecnología para obtener un mejor rendimiento y la confiabilidad.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Introducción al servicio de lenguaje y las extensiones de editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explica cómo crear una extensión para el editor.|  
|[Dentro del editor](../extensibility/inside-the-editor.md)|Describe la estructura general del editor y se enumeran algunas de sus características.|  
|[Managed Extensibility Framework en el editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explica cómo usar Managed Extensibility Framework (MEF) con el editor.|  
|[Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)|Enumera los puntos de extensión del editor. Puntos de extensión representan las características del editor que se pueden extender.|  
|[Tutorial: creación de un elemento de gráfico de vista, comandos y configuración (guías de columnas)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Le guía a través y explica la creación de un elemento de gráfico de vista que dibuja líneas gudie de columna para ayudarle a mantener el código a un ancho de presentación determinado.  También muestra leyendo y escribiendo la configuración, así como declarativo y de implementación de los comandos que se pueden invocar desde la ventana de comandos.|  
|[Importaciones del editor](../extensibility/editor-imports.md)|Enumera los servicios que puede importar una extensión.|  
|[Adaptación del código heredado en el editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Explica los distintos modos para adaptar el código heredado (previamente Visual Studio 2010) para ampliar el editor.|  
|[Migración de un servicio de lenguaje heredado](../extensibility/internals/migrating-a-legacy-language-service.md)|Explica cómo migrar un servicio de lenguaje en función de VSPackage.|  
|[Tutorial: vinculación de un tipo de contenido con una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Muestra cómo vincular un tipo de contenido a una extensión de nombre de archivo.|  
|[Tutorial: creación de un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md)|Muestra cómo agregar un icono a un margen.|  
|[Tutorial: destacado de texto](../extensibility/walkthrough-highlighting-text.md)|Se muestra cómo usar *etiquetas* para resaltar el texto.|  
|[Tutorial: esquematización](../extensibility/walkthrough-outlining.md)|Muestra cómo agregar la esquematización para determinados tipos de llaves.|  
|[Tutorial: visualización de llaves que coincidan](../extensibility/walkthrough-displaying-matching-braces.md)|Muestra cómo se resalta las llaves coincidentes.|  
|[Tutorial: visualización de información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Muestra cómo mostrar elementos emergentes de QuickInfo que describen los elementos de código como propiedades, métodos y eventos.|  
|[Tutorial: visualización de la ayuda de firma](../extensibility/walkthrough-displaying-signature-help.md)|Muestra cómo mostrar elementos emergentes que se proporcionan información sobre el número y tipos de parámetros de una firma.|  
|[Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)|Muestra cómo implementar la finalización de instrucciones.|  
|[Tutorial: implementación de fragmentos de código](../extensibility/walkthrough-implementing-code-snippets.md)|Muestra cómo implementar la expansión del fragmento de código.|  
|[Tutorial: visualización de sugerencias de bombilla](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Muestra cómo mostrar las bombillas para las sugerencias de código.|  
|[Tutorial: uso de un comando de shell con una extensión del editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Muestra cómo asociar un comando de menú en un VSPackage con un componente MEF.|  
|[Tutorial: uso de una tecla de método abreviado con una extensión del editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Muestra cómo asociar un menú contextual en un VSPackage con un componente MEF.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Proporciona información acerca de Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Proporciona información acerca de Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Referencia  
 El editor de Visual Studio incluye los siguientes espacios de nombres.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>

