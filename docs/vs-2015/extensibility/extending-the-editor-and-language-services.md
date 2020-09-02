---
title: Extender el editor y los servicios de lenguaje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 085e1b5c1fbfbbaf5649966738f2864e0b72ed35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674780"
---
# <a name="extending-the-editor-and-language-services"></a>Ampliación del editor y los servicios de lenguaje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede agregar características del servicio de lenguaje (como IntelliSense) a su propio editor y ampliar la mayoría de las características del editor de código de Visual Studio.  Para obtener una lista completa de lo que puede ampliar, consulte [puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md).  
  
 La mayoría de las características del editor se amplían mediante el Managed Extensibility Framework (MEF). Por ejemplo, si la característica del editor que desea extender es el color de la sintaxis, puede escribir una *parte del componente* MEF que defina las clasificaciones para las que desea colorear diferentes colores y cómo desea que se controlen. El editor también admite varias extensiones de la misma característica.  
  
 La capa de presentación del editor se basa en Windows Presentation Framework (WPF). WPF proporciona una biblioteca de gráficos para el formato de texto flexible y también proporciona visualizaciones como gráficos y animaciones.  
  
 El SDK de Visual Studio proporciona adaptadores denominados *correcciones de compatibilidad (Shim* ) para admitir VSPackages que se escribieron para versiones anteriores. No obstante, si tiene un VSPackage existente, se recomienda que lo actualice a la nueva tecnología para obtener un mejor rendimiento y confiabilidad.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Title|Descripción|  
|-----------|-----------------|  
|[Introducción al servicio de lenguaje y las extensiones de editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explica cómo crear una extensión para el editor.|  
|[Dentro del editor](../extensibility/inside-the-editor.md)|Describe la estructura general del editor y enumera algunas de sus características.|  
|[Managed Extensibility Framework en el editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explica cómo usar el Managed Extensibility Framework (MEF) con el editor.|  
|[Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)|Enumera los puntos de extensión del editor. Los puntos de extensión representan las características del editor que se pueden extender.|  
|[Tutorial: creación de un elemento de gráfico de vista, comandos y configuración (guías de columnas)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Describe y explica cómo crear un elemento gráfico de vista que dibuje líneas de Gudie de columnas para ayudarle a mantener el código en un ancho de pantalla determinado.  También muestra la configuración de lectura y escritura, así como la declaración e implementación de comandos que se pueden invocar desde la ventana de comandos.|  
|[Importaciones del editor](../extensibility/editor-imports.md)|Enumera los servicios que una extensión puede importar.|  
|[Adaptación del código heredado en el editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Explica las distintas formas de adaptar el código heredado (anterior a Visual Studio 2010) para extender el editor.|  
|[Migración de un servicio de lenguaje heredado](../extensibility/internals/migrating-a-legacy-language-service.md)|Explica cómo migrar un servicio de lenguaje basado en VSPackage.|  
|[Tutorial: vinculación de un tipo de contenido con una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Muestra cómo vincular un tipo de contenido a una extensión de nombre de archivo.|  
|[Tutorial: creación de un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md)|Muestra cómo agregar un icono a un margen.|  
|[Tutorial: destacado de texto](../extensibility/walkthrough-highlighting-text.md)|Muestra cómo usar *etiquetas* para resaltar texto.|  
|[Tutorial: esquematización](../extensibility/walkthrough-outlining.md)|Muestra cómo agregar la esquematización para tipos específicos de llaves.|  
|[Tutorial: visualización de llaves que coincidan](../extensibility/walkthrough-displaying-matching-braces.md)|Muestra cómo resaltar las llaves coincidentes.|  
|[Tutorial: visualización de información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Muestra cómo mostrar los elementos emergentes de QuickInfo que describen elementos de código como propiedades, métodos y eventos.|  
|[Tutorial: visualización de la ayuda de firma](../extensibility/walkthrough-displaying-signature-help.md)|Muestra cómo mostrar los elementos emergentes que proporcionan información sobre el número y los tipos de parámetros de una firma.|  
|[Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)|Muestra cómo implementar la finalización de instrucciones.|  
|[Tutorial: implementación de fragmentos de código](../extensibility/walkthrough-implementing-code-snippets.md)|Muestra cómo implementar la expansión de fragmentos de código.|  
|[Tutorial: visualización de sugerencias de bombilla](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Muestra cómo mostrar las bombillas para las sugerencias de código.|  
|[Tutorial: uso de un comando de shell con una extensión del editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Muestra cómo asociar un comando de menú en un VSPackage con un componente de MEF.|  
|[Tutorial: uso de una tecla de método abreviado con una extensión del editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Muestra cómo asociar un acceso directo de menú en un VSPackage con un componente de MEF.|  
|[Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Proporciona información sobre el Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](https://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Proporciona información sobre el Windows Presentation Foundation (WPF).|  
  
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
