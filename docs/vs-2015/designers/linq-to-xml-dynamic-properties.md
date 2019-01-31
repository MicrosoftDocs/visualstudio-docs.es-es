---
title: Propiedades dinámicas de LINQ to XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6fce9bca76b604413dc5bd4962760ee4ce08a6ea
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790618"
---
# <a name="linq-to-xml-dynamic-properties"></a>Propiedades dinámicas de LINQ to XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En esta sección se proporciona información de referencia acerca de las propiedades dinámicas en LINQ to XML. Específicamente, esas propiedades son expuestas por las clases <xref:System.Xml.Linq.XAttribute> y <xref:System.Xml.Linq.XElement>, que están en el espacio de nombres <xref:System.Xml.Linq>.  
  
 Tal y como se explica en el tema [Información general de enlace de datos WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), cada una de las propiedades dinámicas es equivalente a un método o una propiedad estándar pública de la misma clase. Esos miembros estándar deben usarse para la mayoría de propósitos; las propiedades dinámicas se proporcionan específicamente para los casos de enlace de datos de LINQ to XML. Para obtener más información acerca de los miembros estándar de esas clases, vea los temas de referencia <xref:System.Xml.Linq.XAttribute> y <xref:System.Xml.Linq.XElement>.  
  
 Con respecto a sus valores resueltos, las propiedades dinámicas de esa sección se dividen en dos categorías:  
  
- Sencillas, como las propiedades `Value` de las clases <xref:System.Xml.Linq.XAttribute> y <xref:System.Xml.Linq.XElement>, que se resuelven en un valor único.  
  
- Valores indexados, como las propiedades [Elements](../designers/elements-xelement-dynamic-property.md) y [Descendants](../designers/descendants-xelement-dynamic-property.md) de <xref:System.Xml.Linq.XElement>, que se resuelven en un tipo de indizador. Para que los tipos de indizador se resuelvan en el valor o la colección que se desea, se les debe pasar un parámetro de nombre expandido.  
  
  Todas las propiedades dinámicas que devuelven un valor indizado del tipo <xref:System.Collections.Generic.IEnumerable%601> utilizan la ejecución aplazada. Para más información sobre la ejecución aplazada, vea [Introducción a las consultas LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="in-this-section"></a>En esta sección  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Propiedades dinámicas de la clase XAttribute](../designers/xattribute-class-dynamic-properties.md)|Proporciona detalles acerca de las propiedades dinámicas expuestas por la clase <xref:System.Xml.Linq.XAttribute>.|  
|[Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)|Proporciona detalles acerca de las propiedades dinámicas expuestas por la clase <xref:System.Xml.Linq.XElement>.|  
  
## <a name="reference"></a>Referencia  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## <a name="see-also"></a>Vea también  
 [Enlace de datos de WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Información general de enlace de datos WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introducción a las consultas LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)
