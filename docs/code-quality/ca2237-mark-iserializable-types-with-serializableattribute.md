---
title: 'CA2237: Marcar los tipos ISerializable con SerializableAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 53d049cad426201a8aaa48662061a4a424116b26
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237942"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Marcar los tipos ISerializable con SerializableAttribute

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|Identificador de comprobación|CA2237|
|Categoría|Microsoft.Usage|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
Un tipo visible externamente implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz y el tipo no está marcado con el <xref:System.SerializableAttribute?displayProperty=fullName> atributo. La regla omite los tipos derivados cuyo tipo base no es serializable.

## <a name="rule-description"></a>Descripción de la regla
Para ser reconocibles por el Common Language Runtime como serializable, los tipos se deben <xref:System.SerializableAttribute> marcar con el atributo incluso si el tipo utiliza una rutina de serialización personalizada <xref:System.Runtime.Serialization.ISerializable> a través de la implementación de la interfaz.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, aplique <xref:System.SerializableAttribute> el atributo al tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima una advertencia de esta regla para las clases de excepción porque deben ser serializables para que funcionen correctamente en todos los dominios de aplicación.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe la regla. Quite la marca <xref:System.SerializableAttribute> de comentario de la línea de atributo para satisfacer la regla.

[!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
[!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2239 Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: Proteger los constructores de serialización](../code-quality/ca2120-secure-serialization-constructors.md)