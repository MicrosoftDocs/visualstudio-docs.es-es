---
title: Herramientas XML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
f1_keywords:
- vb.xmldesigner
helpviewer_keywords:
- XML [Visual Studio], resources
- Enterprise Templates, XML and
- discovery files, XML
- server controls, XML and
- Web server controls, XML
- XSL
- XML [Visual Studio], data sources
- XML schemas
- XML [Visual Studio], SGML relationship to
- CSS, style sheets for XML
- XML [Visual Studio], .NET Framework classes
- data [Visual Studio], XML
- classes [Visual Studio], XML
- style sheets, for XML
- Web services
- SGML, XML
- XML [Visual Studio]
- datasets [Visual Basic], XML Schemas
- XSD schemas
- XSL, style sheets
- XMLDataDocument class
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2812e45460778a3527f55522c6d3fc98285a548d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997325"
---
# <a name="xml-tools-in-visual-studio"></a>Herramientas XML en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Extensible Markup Language (XML) * es un lenguaje de marcado que proporciona un formato para describir los datos. Esto facilita declaraciones más precisas del contenido y resultados de búsqueda más útiles en varias plataformas. Además, XML permite separar la presentación de los datos. Por ejemplo, en HTML se usan etiquetas para indicar al explorador que muestre los datos en negrita o cursiva, pero en XML las etiquetas solo se usan para describir los datos, como el nombre de la ciudad, la temperatura y la presión atmosférica. En XML, para presentar los datos en un explorador se usan las hojas de estilo, como el Lenguaje de hojas de estilo extensible (XSL) y las hojas de estilo CSS. XML separa los datos de la presentación y el proceso. Esto le permite mostrar y procesar los datos como desee por medio de distintas hojas de estilo y aplicaciones.

 XML es un subconjunto de SGML optimizado para entregarse a través de Internet. Lo define World Wide Web Consortium (W3C). Esta estandarización garantiza que los datos estructurados sean uniformes e independientes de las aplicaciones o los proveedores.

 XML es el núcleo de muchas características de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. En la siguiente lista de temas se mencionan las herramientas y características relacionadas con XML que se ofrecen en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Para obtener más información, consulte el [XML Developer Center](http://go.microsoft.com/fwlink/?LinkID=100176), que proporciona la documentación más reciente, información técnica, descargas, grupos de noticias y otros recursos para desarrolladores de XML.

## <a name="in-this-section"></a>En esta sección
 [Trabajar con datos XML](../xml-tools/working-with-xml-data.md) explica el rol de XML en la forma que los datos se controla en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Depuración de XSLT](../xml-tools/debugging-xslt.md) proporciona vínculos a temas sobre cómo usar el depurador de Visual Studio para depurar XSLT.

## <a name="reference"></a>Referencia
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699) expone el [Editor XML](http://go.microsoft.com/fwlink/?LinkId=228249) árbol a través de análisis [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) para cualquier documento XML.

 [Referencia de las normas XML](http://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) proporciona información sobre las tecnologías XML, incluidos XML, definición de tipo de documento (DTD), lenguaje de definición de esquemas XML (XSD) y XSLT.

 <xref:System.Xml?displayProperty=fullName> Describe las clases y otros elementos que componen el <xref:System.Xml> espacio de nombres y proporciona vínculos a información más detallada sobre cada elemento.

 <xref:System.Xml.Serialization?displayProperty=fullName> Describe las clases y otros elementos que componen el <xref:System.Xml.Serialization> espacio de nombres y proporciona vínculos a información más detallada sobre cada elemento.

## <a name="related-sections"></a>Secciones relacionadas
 [Document Object Model (DOM) XML](http://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) describe cómo el <xref:System.Xml.XmlDocument> y sus clases asociadas cumplen con las especificaciones de soporte técnico de espacio de nombres de nivel 2 y W3C Document Object Model (Core) nivel 1.

 [Leer fragmentos de XML con XmlReader](http://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) describe cómo el <xref:System.Xml.XmlReader> proporciona un acceso de solo, de solo lectura sin almacenamiento en caché, hacia delante a los datos XML a través de una secuencia XML.

 [Escribir XML con XmlWriter](http://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) describe cómo el <xref:System.Xml.XmlWriter> proporciona sin almacenamiento en caché, solo hacia delante forma de generar secuencias XML y le ayuda a construir documentos XML que cumplen con el estándar de W3C.

 [Transformaciones XSLT](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) describe cómo el <xref:System.Xml.Xsl.XslCompiledTransform> clase implementa la recomendación XSLT 1.0.

 [Procesar datos XML mediante el modelo de datos XPath](http://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) describe cómo el <xref:System.Xml.XPath.XPathNavigator> clase puede procesar datos XML almacenados en un <xref:System.Xml.XPath.XPathDocument> o un <xref:System.Xml.XmlDocument> objeto. La clase <xref:System.Xml.XPath.XPathNavigator> se basa en el modelo de datos de XQuery 1.0 y XPath 2.0 y se puede usar para navegar por los datos XML y editarlos.

 [Modelo de objetos de esquema XML (SOM)](http://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) describe las clases utilizadas para crear y manipular esquemas XML, proporcionando un <xref:System.Xml.Schema.XmlSchema> clase para cargar y editar un esquema.
