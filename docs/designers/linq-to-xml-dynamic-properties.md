---
title: "Propiedades din&#225;micas de LINQ to XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Propiedades din&#225;micas de LINQ to XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta sección se proporciona información de referencia acerca de las propiedades dinámicas en LINQ to XML.Específicamente, esas propiedades son expuestas por las clases <xref:System.Xml.Linq.XAttribute> y <xref:System.Xml.Linq.XElement>, que están en el espacio de nombres <xref:System.Xml.Linq>.  
  
 Tal y como se explica en el tema [Información general del enlace de datos de WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), cada una de las propiedades dinámicas es equivalente a un método o una propiedad estándar pública de la misma clase.Esos miembros estándar deben usarse para la mayoría de propósitos; las propiedades dinámicas se proporcionan específicamente para los casos de enlace de datos de LINQ to XML.Para obtener más información acerca de los miembros estándar de esas clases, vea los temas de referencia <xref:System.Xml.Linq.XAttribute> y <xref:System.Xml.Linq.XElement>.  
  
 Con respecto a sus valores resueltos, las propiedades dinámicas de esa sección se dividen en dos categorías:  
  
-   Sencillas, como las propiedades `Value` de las clases <xref:System.Xml.Linq.XAttribute> y <xref:System.Xml.Linq.XElement>, que se resuelven en un valor único.  
  
-   Valores indizados, como las propiedades [Elements](../designers/elements-xelement-dynamic-property.md) y [Descendants](../designers/descendants-xelement-dynamic-property.md) de <xref:System.Xml.Linq.XElement>, que se resuelven en un tipo de indizador.Para que los tipos de indizador se resuelvan en el valor o la recopilación que se desea, se les debe pasar un parámetro de nombre expandido.  
  
 Todas las propiedades dinámicas que devuelven un valor indizado del tipo <xref:System.Collections.Generic.IEnumerable%601> utilizan la ejecución aplazada.Para obtener más información sobre la ejecución aplazada, vea [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## En esta sección  
  
|Tema|Descripción|  
|----------|-----------------|  
|[Propiedades dinámicas de la clase XAttribute](../designers/xattribute-class-dynamic-properties.md)|Proporciona detalles acerca de las propiedades dinámicas expuestas por la clase <xref:System.Xml.Linq.XAttribute>.|  
|[Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)|Proporciona detalles acerca de las propiedades dinámicas expuestas por la clase <xref:System.Xml.Linq.XElement>.|  
  
## Referencia  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## Vea también  
 [Enlace de datos de WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Información general sobre el enlace de datos de WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)