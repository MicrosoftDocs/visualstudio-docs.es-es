---
title: Attribute (Propiedad dinámica de XElement)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ec27fe2d7824ca32cbf97dbabac8b7ea6c4aed6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948503"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (Propiedad dinámica de XElement)

Obtiene un indizador que se usa para recuperar la instancia del atributo que se corresponde con el nombre expandido especificado.

## <a name="syntax"></a>Sintaxis

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un indizador del tipo `XAttribute Item(String expandedName)`. Este indizador toma el nombre expandido del atributo especificado y devuelve el elemento <xref:System.Xml.Linq.XAttribute> correspondiente, o bien `null` si no existe ningún atributo con el nombre especificado.

## <a name="remarks"></a>Comentarios

Esta propiedad es equivalente al método <xref:System.Xml.Linq.XElement.Attribute%2A> de la clase <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="see-also"></a>Vea también

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)
- [Valor](../designers/value-xattribute-dynamic-property.md)