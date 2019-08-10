---
title: 'CA2239: Proporcionar métodos de deserialización para campos opcionales'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c0cd59ec30ce45c94ac3422c4271959d74073bff
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920062"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: Proporcionar métodos de deserialización para campos opcionales

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|Identificador de comprobación|CA2239|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
Un tipo tiene un campo que está marcado con el <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> atributo y el tipo no proporciona métodos de control de eventos de deserialización.

## <a name="rule-description"></a>Descripción de la regla
El <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributo no tiene ningún efecto en la serialización; se serializa un campo marcado con el atributo. Sin embargo, el campo se omite en la deserialización y conserva el valor predeterminado asociado a su tipo. Los controladores de eventos de deserialización se deben declarar para establecer el campo durante el proceso de deserialización.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, agregue métodos de control de eventos de deserialización al tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si el campo se debe omitir durante el proceso de deserialización.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo con un campo opcional y métodos de control de eventos de deserialización.

[!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
[!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237: Marcar tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2120: Proteger los constructores de serialización](../code-quality/ca2120-secure-serialization-constructors.md)