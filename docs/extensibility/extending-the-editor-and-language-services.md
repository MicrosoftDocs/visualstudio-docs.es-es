---
title: Ampliación del Editor y los servicios de lenguaje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5e1d8bac8f682017166c3e625aa0578c90515209
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837335"
---
# <a name="extend-the-editor-and-language-services"></a>Ampliar los servicios de editor y lenguaje
Puede agregar características del servicio de lenguaje (por ejemplo, IntelliSense) a su propio editor y ampliar la mayoría de las características del editor de código de Visual Studio.  Para obtener una lista completa de lo que puede extender, consulte [puntos de extensión de editor y el servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md).  
  
 Extender la mayoría de las características de editor mediante el uso de Managed Extensibility Framework (MEF). Por ejemplo, si desea extender la característica del editor es el color de sintaxis, puede escribir un MEF *parte componente* que define las clasificaciones que quiere distintos colores y cómo desea que ellos administran. El editor también admite varias extensiones de la misma característica.  
  
 La capa de presentación del editor se basa Windows Presentation Framework (WPF). WPF proporciona una biblioteca de gráficos para dar formato al texto flexible y también proporciona visualizaciones como gráficos y animaciones.  
  
 El SDK de Visual Studio permite a los adaptadores que se conoce como *las correcciones de compatibilidad* para admitir los VSPackages escritos para versiones anteriores. No obstante, si tiene un VSPackage existente, se recomienda actualizarlo a la nueva tecnología para obtener un mejor rendimiento y la confiabilidad.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Introducción a las extensiones de editor y el servicio de lenguaje](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explica cómo crear una extensión para el editor.|  
|[Dentro del editor](../extensibility/inside-the-editor.md)|Describe la estructura general del editor y se enumeran algunas de sus características.|  
|[Managed Extensibility Framework en el editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explica cómo usar Managed Extensibility Framework (MEF) con el editor.|  
|[Puntos de extensión de editor y el servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)|Enumera los puntos de extensión del editor. Puntos de extensión representan las características del editor que se pueden extender.|  
|[Tutorial: Crear un elemento de gráfico de vista, comandos y configuración (guías de columnas)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Le guía a través y explica la creación de un elemento de gráfico de vista que dibuja líneas de guía de columna para ayudarle a mantener el código a un ancho de presentación determinado.  También muestra leyendo y escribiendo la configuración, así como declarativo y de implementación de los comandos que se pueden invocar desde la ventana de comandos.|  
|[Importaciones del Editor](../extensibility/editor-imports.md)|Enumera los servicios que puede importar una extensión.|  
|[Adaptar código heredado en el editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Explica los distintos modos para adaptar el código heredado (previamente Visual Studio 2010) para ampliar el editor.|  
|[Migrar un servicio de lenguaje heredado](../extensibility/internals/migrating-a-legacy-language-service.md)|Explica cómo migrar un servicio de lenguaje en función de VSPackage.|  
|[Tutorial: Vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Muestra cómo vincular un tipo de contenido a una extensión de nombre de archivo.|  
|[Tutorial: Creación de un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md)|Muestra cómo agregar un icono a un margen.|  
|[Tutorial: Resaltar texto](../extensibility/walkthrough-highlighting-text.md)|Se muestra cómo usar *etiquetas* para resaltar el texto.|  
|[Tutorial: Agregar la esquematización](../extensibility/walkthrough-outlining.md)|Muestra cómo agregar la esquematización para determinados tipos de llaves.|  
|[Tutorial: Mostrar las llaves coincidentes](../extensibility/walkthrough-displaying-matching-braces.md)|Muestra cómo se resalta las llaves coincidentes.|  
|[Tutorial: Mostrar información rápida](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Muestra cómo mostrar elementos emergentes de QuickInfo que describen los elementos de código como propiedades, métodos y eventos.|  
|[Tutorial: Mostrar la Ayuda de firma](../extensibility/walkthrough-displaying-signature-help.md)|Muestra cómo mostrar elementos emergentes que se proporcionan información sobre el número y tipos de parámetros de una firma.|  
|[Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)|Muestra cómo implementar la finalización de instrucciones.|  
|[Tutorial: Implementar los fragmentos de código](../extensibility/walkthrough-implementing-code-snippets.md)|Muestra cómo implementar la expansión del fragmento de código.|  
|[Tutorial: Mostrar sugerencias de bombilla](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Muestra cómo mostrar las bombillas para las sugerencias de código.|  
|[Tutorial: Utilice un comando de shell con una extensión del editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Muestra cómo asociar un comando de menú en un VSPackage con un componente MEF.|  
|[Tutorial: Usar una tecla de método abreviado con una extensión del editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Muestra cómo asociar un menú contextual en un VSPackage con un componente MEF.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Proporciona información acerca de Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Proporciona información acerca de Windows Presentation Foundation (WPF).|  
  
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