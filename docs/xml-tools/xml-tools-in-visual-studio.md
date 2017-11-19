---
title: Herramientas XML en Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.xmldesigner
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
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3786e74f9913400e7a95d962c8512d2263d6ae39
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="xml-tools-in-visual-studio"></a>Herramientas XML en Visual Studio
*Lenguaje de marcado extensible (XML)* es un lenguaje de marcado que proporciona un formato para describir datos. Esto facilita declaraciones más precisas del contenido y resultados de búsqueda más útiles en varias plataformas. Además, XML permite separar la presentación de los datos. Por ejemplo, en HTML se usan etiquetas para indicar al explorador que muestre los datos en negrita o cursiva, pero en XML las etiquetas solo se usan para describir los datos, como el nombre de la ciudad, la temperatura y la presión atmosférica. En XML, para presentar los datos en un explorador se usan las hojas de estilo, como el Lenguaje de hojas de estilo extensible (XSL) y las hojas de estilo CSS. XML separa los datos de la presentación y el proceso. Esto le permite mostrar y procesar los datos como desee por medio de distintas hojas de estilo y aplicaciones.  
  
 XML es un subconjunto de SGML optimizado para entregarse a través de Internet. Lo define World Wide Web Consortium (W3C). Esta estandarización garantiza que los datos estructurados sean uniformes e independientes de las aplicaciones o los proveedores.  
  
 XML es el núcleo de muchas características de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. En la siguiente lista de temas se mencionan las herramientas y características relacionadas con XML que se ofrecen en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Para obtener más información, consulte el [Centro para desarrolladores de XML](http://go.microsoft.com/fwlink/?LinkID=100176), que proporciona lo último en documentación, información técnica, descargas, grupos de noticias y otros recursos para desarrolladores de XML.  
  
## <a name="in-this-section"></a>En esta sección  
 [Trabajo con datos XML](../xml-tools/working-with-xml-data.md)  
 Trata sobre el rol de XML en la manera en que se administran los datos en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Depuración de XSLT](../xml-tools/debugging-xslt.md)  
 Proporciona vínculos a temas sobre el uso del depurador de Visual Studio para depurar XSLT.  
  
## <a name="reference"></a>Referencia  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 Expone el [Editor XML](http://go.microsoft.com/fwlink/?LinkId=228249) árbol a través de análisis [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) para cualquier documento XML.  
  
 [Referencia de los estándares XML](http://msdn.microsoft.com/en-us/79c78508-c9d0-423a-a00f-672e855de401)  
 Proporciona información sobre las tecnologías XML, como XML, DTD (definición de tipo de documento), XSD (lenguaje de definición de esquema XML) y XSLT.  
  
 <xref:System.Xml?displayProperty=fullName>  
 Describe las clases y otros elementos que componen el espacio de nombres <xref:System.Xml> y proporciona vínculos a información más detallada sobre cada elemento.  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 Describe las clases y otros elementos que componen el espacio de nombres <xref:System.Xml.Serialization> y proporciona vínculos a información más detallada sobre cada elemento.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Modelo de objetos de documento (DOM) de XML](/dotnet/standard/data/xml/xml-document-object-model-dom)  
 Describe cómo <xref:System.Xml.XmlDocument> y sus clases asociadas cumplen con las especificaciones de compatibilidad de espacios de nombres de Document Object Model (Core) nivel 1 y nivel 2 de W3C.  
  
 [Leer XML with the XmlReader](http://msdn.microsoft.com/en-us/3029834c-a27e-4331-b7aa-711924062182)  
 Describe cómo <xref:System.Xml.XmlReader> proporciona acceso de solo lectura no almacenado en caché y solo de avance a los datos XML a través de una secuencia XML.  
  
 [Escribir XML con XmlWriter](http://msdn.microsoft.com/en-us/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 Describe cómo <xref:System.Xml.XmlWriter> proporciona un método no almacenado en caché y solo de avance para generar secuencias XML y ayuda a crear documentos XML que cumplen con el estándar de W3C.  
  
 [Transformaciones XSLT](/dotnet/standard/data/xml/xslt-transformations)  
 Describe cómo la clase <xref:System.Xml.Xsl.XslCompiledTransform> implementa la recomendación XSLT 1.0.  
  
 [Procesamiento de datos XML con el modelo de datos XPath](/dotnet/standard/data/xml/process-xml-data-using-the-xpath-data-model)  
 Describe cómo la clase <xref:System.Xml.XPath.XPathNavigator> puede procesar datos XML almacenados en un objeto <xref:System.Xml.XPath.XPathDocument> o <xref:System.Xml.XmlDocument>. La clase <xref:System.Xml.XPath.XPathNavigator> se basa en el modelo de datos de XQuery 1.0 y XPath 2.0 y se puede usar para navegar por los datos XML y editarlos.  
  
 [Modelo de objetos de esquema XML (SOM)](/dotnet/standard/data/xml/xml-schema-object-model-som)  
 Describe las clases usadas para crear y manipular esquemas XML, mediante la especificación de una clase <xref:System.Xml.Schema.XmlSchema> para cargar y editar un esquema.