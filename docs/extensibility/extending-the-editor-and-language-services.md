---
title: Extender el Editor y los servicios de lenguaje | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4113a033d4e1a2595f4a980405e1b39d57d60958
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132579"
---
# <a name="extending-the-editor-and-language-services"></a>Extender el Editor y los servicios de lenguaje
Puede agregar características del servicio de lenguaje (por ejemplo, IntelliSense) a su propio editor y extender la mayoría de las características del editor de código de Visual Studio.  Para obtener una lista completa de lo que puede extender, consulte [servicio de lenguaje y puntos de extensión del Editor de](../extensibility/language-service-and-editor-extension-points.md).  
  
 Ampliar las características de editor mayoría utilizando Managed Extensibility Framework (MEF). Por ejemplo, si la característica de editor que desea extender es el color de sintaxis, puede escribir un MEF *componente* que define las clasificaciones que se desea color diferente y cómo desea controlar. El editor también admite varias extensiones de la misma característica.  
  
 La capa de presentación del editor se basa Windows Presentation Framework (WPF). WPF proporciona una biblioteca de gráficos para dar formato al texto flexible y también proporciona visualizaciones como gráficos y las animaciones.  
  
 El SDK de Visual Studio proporciona adaptadores que se conoce como *correcciones de compatibilidad* para admitir VSPackages escritos para versiones anteriores. No obstante, si tiene un VSPackage existente, se recomienda actualizarla a la nueva tecnología para obtener el mejor rendimiento y confiabilidad.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Introducción al servicio de lenguaje y las extensiones de editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explica cómo crear una extensión para el editor.|  
|[Dentro del editor](../extensibility/inside-the-editor.md)|Describe la estructura general del editor y se enumeran algunas de sus características.|  
|[Managed Extensibility Framework en el editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explica cómo usar Managed Extensibility Framework (MEF) con el editor.|  
|[Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)|Enumera los puntos de extensión del editor. Puntos de extensión representan las características del editor que se pueden extender.|  
|[Tutorial: creación de un elemento de gráfico de vista, comandos y configuración (guías de columnas)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Le guía a través de y se explica la creación de un elemento de gráfico de vista que dibuja líneas de gudie de columna para ayudarle a mantener el código para un determinado ancho de pantalla.  También muestra leyendo y escribiendo la configuración, así como declarar e implementar los comandos que pueden invocar desde la ventana de comandos.|  
|[Importaciones del editor](../extensibility/editor-imports.md)|Enumera los servicios que puede importar una extensión.|  
|[Adaptar el código heredado en el Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Explica los distintos modos para adaptar el código heredado (previamente Visual Studio 2010) para ampliar el editor.|  
|[Migración de un servicio de lenguaje heredado](../extensibility/internals/migrating-a-legacy-language-service.md)|Explica cómo migrar un servicio de lenguaje en función de VSPackage.|  
|[Tutorial: vinculación de un tipo de contenido con una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Muestra cómo vincular un tipo de contenido a una extensión de nombre de archivo.|  
|[Tutorial: creación de un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md)|Muestra cómo agregar un icono a un margen.|  
|[Tutorial: destacado de texto](../extensibility/walkthrough-highlighting-text.md)|Muestra cómo utilizar *etiquetas* para resaltar el texto.|  
|[Tutorial: esquematización](../extensibility/walkthrough-outlining.md)|Muestra cómo agregar la esquematización para determinados tipos de llaves.|  
|[Tutorial: visualización de llaves que coincidan](../extensibility/walkthrough-displaying-matching-braces.md)|Muestra cómo se resalta las llaves coincidentes.|  
|[Tutorial: visualización de información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Muestra cómo mostrar elementos emergentes de QuickInfo que describen los elementos de código como propiedades, métodos y eventos.|  
|[Tutorial: visualización de la ayuda de firma](../extensibility/walkthrough-displaying-signature-help.md)|Muestra cómo mostrar elementos emergentes que aportan información sobre el número y los tipos de parámetros en una firma.|  
|[Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)|Muestra cómo implementar la finalización de instrucciones.|  
|[Tutorial: implementación de fragmentos de código](../extensibility/walkthrough-implementing-code-snippets.md)|Muestra cómo implementar la expansión de fragmento de código.|  
|[Tutorial: visualización de sugerencias de bombilla](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Muestra cómo mostrar las bombillas para obtener sugerencias de código.|  
|[Tutorial: uso de un comando de shell con una extensión del editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Muestra cómo asociar un comando de menú en un paquete VSPackage a un componente MEF.|  
|[Tutorial: uso de una tecla de método abreviado con una extensión del editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Muestra cómo asociar un menú contextual en un paquete VSPackage a un componente MEF.|  
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