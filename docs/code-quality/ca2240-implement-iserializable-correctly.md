---
title: 'CA2240: Implementar ISerializable correctamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9ef3e012b3a818c60be23278fe622a40330f3b43
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541485"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Implementar ISerializable correctamente

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|Identificador de comprobación|CA2240|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un tipo visible externamente es asignable a la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz y una de las siguientes condiciones es true:

- El tipo hereda pero no invalida el <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método y el tipo declara campos de instancia que no están marcados con el <xref:System.NonSerializedAttribute?displayProperty=fullName> atributo.

- El tipo no está sellado y el tipo implementa un <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método que no es externamente visible y reemplazable.

## <a name="rule-description"></a>Descripción de la regla
 Los campos que se declaran en un tipo que hereda de la instancia la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz no se incluyen automáticamente en el proceso de serialización. Para incluir los campos, el tipo debe implementar la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método y el constructor de serialización. Si no se deben serializar los campos, aplicar el <xref:System.NonSerializedAttribute> a los campos para indicar explícitamente la decisión de atributo.

 En los tipos que no están sellados, las implementaciones de la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método debe ser visible externamente. Por lo tanto, el método se puede llamar a tipos derivados y es reemplazable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, asegúrese del <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método visible y reemplazable y asegúrese de que todos los campos de instancia se incluyen en el proceso de serialización o se marca explícitamente con la <xref:System.NonSerializedAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra dos tipos serializables que infringen la regla.

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se corrige las dos anteriores infracciones proporcionando una implementación reemplazable de <xref:System.Runtime.Serialization.ISerializable.GetObjectData> en la clase Book y proporcionando una implementación de `GetObjectData` en la clase de biblioteca.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120: Proteger los constructores de serialización](../code-quality/ca2120-secure-serialization-constructors.md)