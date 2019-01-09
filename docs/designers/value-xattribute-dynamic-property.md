---
title: Value (Propiedad dinámica de XAttribute)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b97e33bdcb28a3c8790af752d5ab9786dc5ef3d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882898"
---
# <a name="value-xattribute-dynamic-property"></a>Value (Propiedad dinámica de XAttribute)

Obtiene o establece el valor del atributo XML.

## <a name="syntax"></a>Sintaxis

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

<xref:System.String> que contiene el valor de este atributo.

## <a name="exceptions"></a>Excepciones

|Tipo de excepción|Condición|
| - |---------------|
|<xref:System.ArgumentNullException>|Cuando se establece, el parámetro `value` es `null`.|

## <a name="remarks"></a>Comentarios

Esta propiedad es equivalente a la propiedad <xref:System.Xml.Linq.XAttribute.Value%2A> de la clase <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, pero su propiedad dinámica también admite las notificaciones de cambio.

## <a name="see-also"></a>Vea también

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Propiedades dinámicas de la clase XAttribute](../designers/xattribute-class-dynamic-properties.md)
- [Attribute](../designers/attribute-xelement-dynamic-property.md)