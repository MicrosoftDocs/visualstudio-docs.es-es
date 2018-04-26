---
title: Elements (Propiedad dinámica de XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4100e26d07b9dc76f9947e4f5a5f7db3a901abe2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="elements-xelement-dynamic-property"></a>Elements (Propiedad dinámica de XElement)

Obtiene un indizador que se utiliza para recuperar los elementos secundarios del elemento actual que coinciden con el nombre expandido especificado.

## <a name="syntax"></a>Sintaxis

```
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un indizador del tipo `IEnumerable<XElement> Item(String expandedName)`. Este indizador toma el nombre expandido de los elementos secundarios deseados y devuelve los elementos secundarios coincidentes en una recopilación <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Comentarios

Esta propiedad es equivalente al método <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> de la clase <xref:System.Xml.Linq.XContainer>.

Los elementos de la colección devuelta están en el orden del documento de origen XML.

Esta propiedad usa la ejecución aplazada.

## <a name="see-also"></a>Vea también

- [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)
- [Element](../designers/element-xelement-dynamic-property.md)
- [Descendants](../designers/descendants-xelement-dynamic-property.md)