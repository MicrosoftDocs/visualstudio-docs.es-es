---
title: Xml (Propiedad dinámica de XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d58dea02a45ccc84e7829da2acdb479eb17dda3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931252"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (propiedad dinámica de XElement)

Obtiene el contenido XML sin formato del elemento.

## <a name="syntax"></a>Sintaxis

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

Un <xref:System.String> que representa el contenido XML sin formato del elemento.

## <a name="remarks"></a>Comentarios

Esta propiedad es equivalente al método <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> de la clase <xref:System.Xml.Linq.XNode?displayProperty=fullName>, con el parámetro `SaveOptions` establecido en <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Vea también

- [Propiedades dinámicas de la clase XElement](../designers/xelement-class-dynamic-properties.md)
- [Valor](../designers/value-xelement-dynamic-property.md)