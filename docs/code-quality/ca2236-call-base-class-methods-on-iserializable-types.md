---
title: 'CA2236: Llamar a métodos de clase base en tipos ISerializable'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a9a3070abc1f2bab3f3658589db54b656a635e2b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238077"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Llamar a métodos de clase base en tipos ISerializable

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|Identificador de comprobación|CA2236|
|Categoría|Microsoft.Usage|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
Un tipo se deriva de un tipo que implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz y se cumple una de las condiciones siguientes:

- El tipo implementa el constructor de serialización, es decir, un constructor con la <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>firma <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> del parámetro, pero no llama al constructor de serialización del tipo base.

- El tipo implementa el <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método pero no llama al <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método del tipo base.

## <a name="rule-description"></a>Descripción de la regla
En un proceso de serialización personalizado, un tipo implementa el <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método para serializar sus campos y el constructor de serialización para deserializar los campos. Si el tipo se deriva de un tipo que implementa la <xref:System.Runtime.Serialization.ISerializable> interfaz, se debe llamar al método de tipo <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> base y al constructor de serialización para serializar o deserializar los campos del tipo base. De lo contrario, el tipo no se serializará y deserializará correctamente. Tenga en cuenta que si el tipo derivado no agrega ningún campo nuevo, el tipo no necesita implementar el <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método ni el constructor de serialización ni llamar a los equivalentes de tipo base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, llame al método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> de tipo base o al constructor de serialización desde el constructor o el método de tipo derivado correspondiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo derivado que satisface la regla llamando al constructor de serialización <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> y al método de la clase base.

[!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
[!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237: Marcar tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2239 Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: Proteger los constructores de serialización](../code-quality/ca2120-secure-serialization-constructors.md)