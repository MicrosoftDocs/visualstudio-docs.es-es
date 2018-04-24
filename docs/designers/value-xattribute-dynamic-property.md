---
title: Value (Propiedad dinámica de XAttribute)
ms.date: 11/04/2016
ms.technology: vs-ide-designers
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
ms.openlocfilehash: 3b98272fe2c86137eb925a54924e1b0e8411ed0e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="value-xattribute-dynamic-property"></a>Value (Propiedad dinámica de XAttribute)

Obtiene o establece el valor del atributo XML.

## <a name="syntax"></a>Sintaxis

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto

<xref:System.String> que contiene el valor de este atributo.

## <a name="exceptions"></a>Excepciones

|Tipo de excepción|Condición|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|Cuando se establece, el parámetro `value` es `null`.|

## <a name="remarks"></a>Comentarios

Esta propiedad es equivalente a la propiedad <xref:System.Xml.Linq.XAttribute.Value%2A> de la clase <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, pero su propiedad dinámica también admite las notificaciones de cambio.

## <a name="see-also"></a>Vea también

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Propiedades dinámicas de la clase XAttribute](../designers/xattribute-class-dynamic-properties.md)
- [Attribute](../designers/attribute-xelement-dynamic-property.md)