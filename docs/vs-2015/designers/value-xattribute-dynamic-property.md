---
title: Value (Propiedad dinámica de XAttribute) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9a31b4c4182ed67a3e67d3c25c2c5ccf50e083f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664050"
---
# <a name="value-xattribute-dynamic-property"></a>Value (Propiedad dinámica de XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName> [atributo](../designers/attribute-xelement-dynamic-property.md) de [propiedades dinámicas de la clase XAttribute](../designers/xattribute-class-dynamic-properties.md)
