---
title: Propiedades dinámicas de LINQ to XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abad2e8966bfc9fc2926c1ca985e1cb5450f1d68
ms.sourcegitcommit: e5a382de633156b85b292f35e3d740f817715d47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2018
ms.locfileid: "38978143"
---
# <a name="linq-to-xml-dynamic-properties"></a>Propiedades dinámicas de LINQ to XML

En esta sección se proporciona información de referencia acerca de las propiedades dinámicas en LINQ to XML. Específicamente, esas propiedades son expuestas por las clases <xref:System.Xml.Linq.XAttribute> y <xref:System.Xml.Linq.XElement>, que están en el espacio de nombres <xref:System.Xml.Linq>.

Tal y como se explica en el tema [Información general de enlace de datos WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), cada una de las propiedades dinámicas es equivalente a un método o una propiedad estándar pública de la misma clase. Esos miembros estándar deben usarse para la mayoría de propósitos; las propiedades dinámicas se proporcionan específicamente para los casos de enlace de datos de LINQ to XML. Para obtener más información acerca de los miembros estándar de esas clases, vea los temas de referencia <xref:System.Xml.Linq.XAttribute> y <xref:System.Xml.Linq.XElement>.

Con respecto a sus valores resueltos, las propiedades dinámicas de esa sección se dividen en dos categorías:

- Sencillas, como las propiedades `Value` de las clases <xref:System.Xml.Linq.XAttribute> y <xref:System.Xml.Linq.XElement>, que se resuelven en un valor único.

- Valores indexados, como las propiedades [Elements](../designers/elements-xelement-dynamic-property.md) y [Descendants](../designers/descendants-xelement-dynamic-property.md) de <xref:System.Xml.Linq.XElement>, que se resuelven en un tipo de indizador. Para que los tipos de indizador se resuelvan en el valor o la colección que se desea, se les debe pasar un parámetro de nombre expandido.

Todas las propiedades dinámicas que devuelven un valor indizado del tipo <xref:System.Collections.Generic.IEnumerable%601> utilizan la ejecución aplazada. Para obtener más información sobre la ejecución aplazada, vea [Introducción a las consultas LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).

## <a name="reference"></a>Referencia

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Vea también

- [Enlace de datos de WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Información general de enlace de datos WPF con LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)
- [Introducción a las consultas LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
