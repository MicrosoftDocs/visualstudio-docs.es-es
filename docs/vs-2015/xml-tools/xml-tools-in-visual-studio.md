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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ee0cf61f8ec2787894c6f67b8ac75424246c507
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297449"
---
# <a name="xml-tools-in-visual-studio"></a>Herramientas XML en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Extensible Markup Language (XML)* is a markup language that provides a format for describing data. Esto facilita declaraciones más precisas del contenido y resultados de búsqueda más útiles en varias plataformas. Además, XML permite separar la presentación de los datos. Por ejemplo, en HTML se usan etiquetas para indicar al explorador que muestre los datos en negrita o cursiva, pero en XML las etiquetas solo se usan para describir los datos, como el nombre de la ciudad, la temperatura y la presión atmosférica. En XML, para presentar los datos en un explorador se usan las hojas de estilo, como el Lenguaje de hojas de estilo extensible (XSL) y las hojas de estilo CSS. XML separa los datos de la presentación y el proceso. Esto le permite mostrar y procesar los datos como desee por medio de distintas hojas de estilo y aplicaciones.

 XML es un subconjunto de SGML optimizado para entregarse a través de Internet. Lo define World Wide Web Consortium (W3C). Esta estandarización garantiza que los datos estructurados sean uniformes e independientes de las aplicaciones o los proveedores.

 XML es el núcleo de muchas características de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. En la siguiente lista de temas se mencionan las herramientas y características relacionadas con XML que se ofrecen en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 For more information, see the [XML Developer Center](https://go.microsoft.com/fwlink/?LinkID=100176), which provides the latest documentation, technical information, downloads, newsgroups, and other resources for XML developers.

## <a name="in-this-section"></a>En esta sección
 [Working with XML Data](../xml-tools/working-with-xml-data.md) Discusses the role of XML in the way data is handled in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 [Debugging XSLT](../xml-tools/debugging-xslt.md) Provides links to topics about using the Visual Studio debugger to debug XSLT.

## <a name="reference"></a>Referencia
 [Microsoft.VisualStudio.XmlEditor](https://go.microsoft.com/fwlink/?LinkID=165699) Exposes the [XML Editor](https://go.microsoft.com/fwlink/?LinkId=228249) parse tree through [System.Xml.Linq](https://go.microsoft.com/fwlink/?LinkId=228250) for any XML documents.

 [XML Standards Reference](https://msdn.microsoft.com/79c78508-c9d0-423a-a00f-672e855de401) Provides information about XML technologies, including XML, Document Type Definition (DTD), XML Schema definition language (XSD), and XSLT.

 <xref:System.Xml?displayProperty=fullName> Describes the classes and other elements that make up the <xref:System.Xml> namespace and provides links to more detailed information on each item.

 <xref:System.Xml.Serialization?displayProperty=fullName> Describes the classes and other elements that make up the <xref:System.Xml.Serialization> namespace and provides links to more detailed information about each item.

## <a name="related-sections"></a>Secciones relacionadas
 [XML Document Object Model (DOM)](https://msdn.microsoft.com/library/b5e52844-4820-47c0-a61d-de2da33e9f54) Describes how the <xref:System.Xml.XmlDocument> and its associated classes comply with the W3C Document Object Model (Core) Level 1 and Level 2 namespace support specifications.

 [Reading XML with the XmlReader](https://msdn.microsoft.com/3029834c-a27e-4331-b7aa-711924062182) Describes how the <xref:System.Xml.XmlReader> provides noncached, forward only, read-only access to XML data over an XML stream.

 [Writing XML with the XmlWriter](https://msdn.microsoft.com/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86) Describes how the <xref:System.Xml.XmlWriter> provides noncached, forward only, way of generating XML streams and helps you build XML documents that comply with the W3C standard.

 [XSLT Transformations](https://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03) Describes how the <xref:System.Xml.Xsl.XslCompiledTransform> class implements the XSLT 1.0 recommendation.

 [Process XML Data Using the XPath Data Model](https://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081) Describes how the <xref:System.Xml.XPath.XPathNavigator> class can process XML data stored in an <xref:System.Xml.XPath.XPathDocument> or an <xref:System.Xml.XmlDocument> object. La clase <xref:System.Xml.XPath.XPathNavigator> se basa en el modelo de datos de XQuery 1.0 y XPath 2.0 y se puede usar para navegar por los datos XML y editarlos.

 [XML Schema Object Model (SOM)](https://msdn.microsoft.com/library/a897a599-ffd1-43f9-8807-e58c8a7194cd) Describes the classes used for creating and manipulating XML Schemas, by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.
