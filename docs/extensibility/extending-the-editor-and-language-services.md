---
title: Ampliación de los servicios de editor y lenguaje Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 239c638ec32cc0dc2b2e275a5dbe0c4213a3423e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711710"
---
# <a name="extend-the-editor-and-language-services"></a>Ampliar el editor y los servicios de idiomas
Puede agregar características de servicio de lenguaje (como IntelliSense) a su propio editor y ampliar la mayoría de las características del editor de código de Visual Studio.  Para obtener una lista completa de lo que puede ampliar, consulte Servicio de lenguaje [y puntos](../extensibility/language-service-and-editor-extension-points.md)de extensión del editor.

 La mayoría de las características del editor se amplían mediante Managed Extensibility Framework (MEF). Por ejemplo, si la característica del editor que desea ampliar es la coloración de sintaxis, puede escribir una parte del *componente* MEF que defina las clasificaciones para las que desea colorear diferente y cómo desea que se manejen. El editor también admite varias extensiones de la misma característica.

 La capa de presentación del editor se basa en Windows Presentation Framework (WPF). WPFWPF proporciona una biblioteca de gráficos para el formato de texto flexible y también proporciona visualizaciones como gráficos y animaciones.

 El SDK de Visual Studio proporciona adaptadores conocidos como *compatibilidades* para admitir VSPackages que se escribieron para versiones anteriores. Sin embargo, si tiene un VSPackage existente, se recomienda actualizarlo a la nueva tecnología para obtener un mejor rendimiento y confiabilidad.

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Comience con el servicio de lenguaje y las extensiones del editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Explica cómo crear una extensión para el editor.|
|[Dentro del editor](../extensibility/inside-the-editor.md)|Describe la estructura general del editor y enumera algunas de sus características.|
|[Managed Extensibility Framework en el editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Explica cómo usar Managed Extensibility Framework (MEF) con el editor.|
|[Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)|Enumera los puntos de extensión del editor. Los puntos de extensión representan las características del editor que se pueden ampliar.|
|[Tutorial: Crear un adorno de vista, comandos y configuración (guías de columna)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Recorre y explica la creación de un adorno de vista que dibuja líneas guía de columna para ayudarle a mantener el código en un determinado ancho de pantalla.  También muestra la configuración de lectura y escritura, así como la declaración e implementación de comandos que se pueden invocar desde la ventana de comandos.|
|[Importaciones de editores](../extensibility/editor-imports.md)|Enumera los servicios que puede importar una extensión.|
|[Adaptar el código heredado al editor](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|Explica diferentes formas de adaptar el código heredado (anterior a Visual Studio 2010) para ampliar el editor.|
|[Migrar un servicio de lenguaje heredado](../extensibility/internals/migrating-a-legacy-language-service.md)|Explica cómo migrar un servicio de lenguaje basado en VSPackage.|
|[Tutorial: Vincule un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Muestra cómo vincular un tipo de contenido a una extensión de nombre de archivo.|
|[Tutorial: Crear un glifo de margen](../extensibility/walkthrough-creating-a-margin-glyph.md)|Muestra cómo agregar un icono a un margen.|
|[Tutorial: Resaltar texto](../extensibility/walkthrough-highlighting-text.md)|Muestra cómo utilizar *etiquetas* para resaltar texto.|
|[Tutorial: Agregar esquematización](../extensibility/walkthrough-outlining.md)|Muestra cómo agregar esquematización para tipos específicos de llaves.|
|[Tutorial: Mostrar llaves coincidentes](../extensibility/walkthrough-displaying-matching-braces.md)|Muestra cómo resaltar llaves coincidentes.|
|[Tutorial: Mostrar información sobre herramientas quickInfo](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Muestra cómo mostrar ventanas emergentes de QuickInfo que describen elementos de código como propiedades, métodos y eventos.|
|[Tutorial: Mostrar la ayuda de firma](../extensibility/walkthrough-displaying-signature-help.md)|Muestra cómo mostrar ventanas emergentes que proporcionan información sobre el número y los tipos de parámetros de una firma.|
|[Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)|Muestra cómo implementar la finalización de instrucciones.|
|[Tutorial: Implementar fragmentos de código](../extensibility/walkthrough-implementing-code-snippets.md)|Muestra cómo implementar la expansión de fragmento de código.|
|[Tutorial: Mostrar sugerencias de bombillas](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Muestra cómo mostrar bombillas para sugerencias de código.|
|[Tutorial: Utilice un comando shell con una extensión de editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Muestra cómo asociar un comando de menú en un VSPackage con un componente MEF.|
|[Tutorial: Use una tecla de método abreviado con una extensión de editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Muestra cómo asociar un acceso directo de menú en un VSPackage con un componente MEF.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Proporciona información sobre Managed Extensibility Framework (MEF).|
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
