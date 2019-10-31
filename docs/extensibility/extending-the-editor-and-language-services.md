---
title: Extender el editor y los servicios de lenguaje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af1fa0222be9630a495a43204d7a973341190131
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186669"
---
# <a name="extend-the-editor-and-language-services"></a>Extender el editor y los servicios de lenguaje
Puede agregar características del servicio de lenguaje (como IntelliSense) a su propio editor y ampliar la mayoría de las características del editor de código de Visual Studio.  Para obtener una lista completa de lo que puede ampliar, consulte [puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md).

 La mayoría de las características del editor se amplían mediante el Managed Extensibility Framework (MEF). Por ejemplo, si la característica del editor que desea extender es el color de la sintaxis, puede escribir una *parte del componente* MEF que defina las clasificaciones para las que desea colorear diferentes colores y cómo desea que se controlen. El editor también admite varias extensiones de la misma característica.

 La capa de presentación del editor se basa en Windows Presentation Framework (WPF). WPF proporciona una biblioteca de gráficos para el formato de texto flexible y también proporciona visualizaciones como gráficos y animaciones.

 El SDK de Visual Studio proporciona adaptadores denominados *correcciones de compatibilidad (Shim* ) para admitir VSPackages que se escribieron para versiones anteriores. No obstante, si tiene un VSPackage existente, se recomienda que lo actualice a la nueva tecnología para obtener un mejor rendimiento y confiabilidad.

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Introducción al servicio de lenguaje y extensiones de editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explica cómo crear una extensión para el editor.|
|[Dentro del editor](../extensibility/inside-the-editor.md)|Describe la estructura general del editor y enumera algunas de sus características.|
|[Managed Extensibility Framework en el editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explica cómo usar el Managed Extensibility Framework (MEF) con el editor.|
|[Puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)|Enumera los puntos de extensión del editor. Los puntos de extensión representan las características del editor que se pueden extender.|
|[Tutorial: crear un elemento gráfico de vista, comandos y configuración (guías de columnas)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Recorre y explica cómo crear un elemento gráfico de vistas que dibuja las líneas de guía de columna para ayudarle a mantener el código en un determinado ancho de pantalla.  También muestra la configuración de lectura y escritura, así como la declaración e implementación de comandos que se pueden invocar desde la ventana de comandos.|
|[Importaciones del editor](../extensibility/editor-imports.md)|Enumera los servicios que una extensión puede importar.|
|[Adaptación del código heredado al editor](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|Explica las distintas formas de adaptar el código heredado (anterior a Visual Studio 2010) para extender el editor.|
|[Migración de un servicio de lenguaje heredado](../extensibility/internals/migrating-a-legacy-language-service.md)|Explica cómo migrar un servicio de lenguaje basado en VSPackage.|
|[Tutorial: vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Muestra cómo vincular un tipo de contenido a una extensión de nombre de archivo.|
|[Tutorial: crear un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md)|Muestra cómo agregar un icono a un margen.|
|[Tutorial: resaltar texto](../extensibility/walkthrough-highlighting-text.md)|Muestra cómo usar *etiquetas* para resaltar texto.|
|[Tutorial: agregar esquematización](../extensibility/walkthrough-outlining.md)|Muestra cómo agregar la esquematización para tipos específicos de llaves.|
|[Tutorial: Mostrar llaves coincidentes](../extensibility/walkthrough-displaying-matching-braces.md)|Muestra cómo resaltar las llaves coincidentes.|
|[Tutorial: Mostrar información sobre herramientas de QuickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Muestra cómo mostrar los elementos emergentes de QuickInfo que describen elementos de código como propiedades, métodos y eventos.|
|[Tutorial: Mostrar ayuda para las firmas](../extensibility/walkthrough-displaying-signature-help.md)|Muestra cómo mostrar los elementos emergentes que proporcionan información sobre el número y los tipos de parámetros de una firma.|
|[Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)|Muestra cómo implementar la finalización de instrucciones.|
|[Tutorial: implementar fragmentos de código](../extensibility/walkthrough-implementing-code-snippets.md)|Muestra cómo implementar la expansión de fragmentos de código.|
|[Tutorial: Mostrar sugerencias de bombillas](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Muestra cómo mostrar las bombillas para las sugerencias de código.|
|[Tutorial: usar un comando de Shell con una extensión de editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Muestra cómo asociar un comando de menú en un VSPackage con un componente de MEF.|
|[Tutorial: usar una tecla de método abreviado con una extensión de editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Muestra cómo asociar un acceso directo de menú en un VSPackage con un componente de MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Proporciona información sobre el Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Proporciona información sobre el Windows Presentation Foundation (WPF).|

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