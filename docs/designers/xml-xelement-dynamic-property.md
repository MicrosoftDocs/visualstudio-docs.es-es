---
title: Xml (Propiedad dinámica de XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0cadfd6f02cbe431cb5a74db4a3b7008d05d9c05
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026988"
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