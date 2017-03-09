---
title: "Herramientas XML en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.xmldesigner"
helpviewer_keywords: 
  - "clases [Visual Studio], XML"
  - "CSS, hojas de estilos para XML"
  - "datos [Visual Studio], XML"
  - "conjuntos de datos [Visual Basic], esquemas XML"
  - "archivos de detección, XML"
  - "Enterprise Templates, XML y"
  - "controles de servidor, XML y"
  - "SGML, XML"
  - "hojas de estilos, para XML"
  - "controles de servidor web, XML"
  - "servicios Web"
  - "XML [Visual Studio]"
  - "XML [Visual Studio], clases de .NET Framework"
  - "XML [Visual Studio], orígenes de datos"
  - "XML [Visual Studio], recursos"
  - "XML [Visual Studio], relación con SGML"
  - "esquemas XML"
  - "XMLDataDocument (clase)"
  - "esquemas XSD"
  - "XSL"
  - "XSL, hojas de estilos"
ms.assetid: 1fd5de47-2d61-4180-9539-c2c4bf9ab768
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Herramientas XML en Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El *lenguaje de marcado extensible \(XML\)* es un lenguaje de marcado que proporciona un formato para describir datos.  Esto facilita declaraciones más precisas del contenido y resultados de búsqueda más útiles en varias plataformas.  Además, XML permite separar la presentación de los datos.  Por ejemplo, en HTML se usan etiquetas para indicar al explorador que muestre los datos en negrita o cursiva, pero en XML las etiquetas solo se usan para describir los datos, como el nombre de la ciudad, la temperatura y la presión atmosférica.  En XML, para presentar los datos en un explorador se usan las hojas de estilo, como el Lenguaje de hojas de estilo extensible \(XSL\) y las hojas de estilo CSS.  XML separa los datos de la presentación y el proceso.  Esto le permite mostrar y procesar los datos como desee por medio de distintas hojas de estilo y aplicaciones.  
  
 XML es un subconjunto de SGML optimizado para entregarse a través de Internet.  Lo define World Wide Web Consortium \(W3C\).  Esta estandarización garantiza que los datos estructurados sean uniformes e independientes de las aplicaciones o los proveedores.  
  
 XML es el núcleo de muchas características de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  En la siguiente lista de temas se mencionan las herramientas y características relacionadas con XML que se ofrecen en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 Para obtener más información, vea el [Centro para desarrolladores de XML](http://go.microsoft.com/fwlink/?LinkID=100176), que proporciona lo último en documentación, información técnica, descargas, grupos de noticias y otros recursos para desarrolladores de XML.  
  
## En esta sección  
 [Trabajo con datos XML](../xml-tools/working-with-xml-data.md)  
 Trata sobre el rol de XML en la manera en que se administran los datos en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Depuración de XSLT](../xml-tools/debugging-xslt.md)  
 Proporciona vínculos a temas sobre el uso del depurador de Visual Studio para depurar XSLT.  
  
## Referencia  
 [Microsoft.VisualStudio.XmlEditor](http://go.microsoft.com/fwlink/?LinkID=165699)  
 Expone el árbol de análisis del [Editor XML](http://go.microsoft.com/fwlink/?LinkId=228249) a través de [System.Xml.Linq](http://go.microsoft.com/fwlink/?LinkId=228250) para cualquier documento XML.  
  
 [Referencia de las normas XML](http://msdn.microsoft.com/es-es/79c78508-c9d0-423a-a00f-672e855de401)  
 Proporciona información sobre las tecnologías XML, como XML, DTD \(definición de tipo de documento\), XSD \(lenguaje de definición de esquema XML\) y XSLT.  
  
 <xref:System.Xml?displayProperty=fullName>  
 Describe las clases y otros elementos que componen el espacio de nombres <xref:System.Xml> y proporciona vínculos a información más detallada sobre cada elemento.  
  
 <xref:System.Xml.Serialization?displayProperty=fullName>  
 Describe las clases y otros elementos que componen el espacio de nombres <xref:System.Xml.Serialization> y proporciona vínculos a información más detallada sobre cada elemento.  
  
## Secciones relacionadas  
 [Modelo de objetos de documento XML \(DOM\)](../Topic/XML%20Document%20Object%20Model%20\(DOM\).md)  
 Describe cómo <xref:System.Xml.XmlDocument> y sus clases asociadas cumplen con las especificaciones de compatibilidad de espacios de nombres de Document Object Model \(Core\) nivel 1 y nivel 2 de W3C.  
  
 [Reading XML with the XmlReader](http://msdn.microsoft.com/es-es/3029834c-a27e-4331-b7aa-711924062182)  
 Describe cómo <xref:System.Xml.XmlReader> proporciona acceso de solo lectura no almacenado en caché y solo de avance a los datos XML a través de una secuencia XML.  
  
 [Writing XML with the XmlWriter](http://msdn.microsoft.com/es-es/ea41f72c-e1d3-4e0a-ab0f-f0eb1c27ab86)  
 Describe cómo <xref:System.Xml.XmlWriter> proporciona un método no almacenado en caché y solo de avance para generar secuencias XML y ayuda a crear documentos XML que cumplen con el estándar de W3C.  
  
 [Transformaciones XSLT](../Topic/XSLT%20Transformations.md)  
 Describe cómo la clase <xref:System.Xml.Xsl.XslCompiledTransform> implementa la recomendación XSLT 1.0.  
  
 [Procesamiento de datos XML con el modelo de datos XPath](../Topic/Process%20XML%20Data%20Using%20the%20XPath%20Data%20Model.md)  
 Describe cómo la clase <xref:System.Xml.XPath.XPathNavigator> puede procesar datos XML almacenados en un objeto <xref:System.Xml.XPath.XPathDocument> o <xref:System.Xml.XmlDocument>.  La clase <xref:System.Xml.XPath.XPathNavigator> se basa en el modelo de datos de XQuery 1.0 y XPath 2.0 y se puede usar para navegar por los datos XML y editarlos.  
  
 [Modelo de objetos de esquema XML \(SOM\)](../Topic/XML%20Schema%20Object%20Model%20\(SOM\).md)  
 Describe las clases usadas para crear y manipular esquemas XML, mediante la especificación de una clase <xref:System.Xml.Schema.XmlSchema> para cargar y editar un esquema.