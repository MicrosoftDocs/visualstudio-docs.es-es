---
title: 'LCA2236: Llamar a métodos de clase base en tipos ISerializable'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7bc90dfd0cf786bbd4e2494a6c65e2c19ff4eb6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>LCA2236: Llamar a métodos de clase base en tipos ISerializable
|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|Identificador de comprobación|CA2236|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo deriva de un tipo que implementa el <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz y una de las siguientes condiciones es true:

-   El tipo implementa el constructor de serialización, es decir, un constructor con la <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> firma del parámetro, pero no se llame al constructor de serialización del tipo base.

-   El tipo implementa la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método pero no llama a la <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método del tipo base.

## <a name="rule-description"></a>Descripción de la regla
 En un proceso de serialización personalizado, un tipo implementa el <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método serializar sus campos y el constructor de serialización para deserializar los campos. Si el tipo se deriva de un tipo que implementa el <xref:System.Runtime.Serialization.ISerializable> de la interfaz, el tipo base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> constructor de serialización y el método debe llamarse para serializar/desinstalación-serialize los campos del tipo base. En caso contrario, el tipo no se serializa y deserializa correctamente. Tenga en cuenta que si el tipo derivado no agrega ningún campo nuevo, el tipo no tiene que implementar el <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método ni el constructor de serialización o llamar a los equivalentes de tipo base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame al tipo base <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> constructor de serialización o de método desde correspondiente derivado constructor o el método de tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo derivado que cumple la regla llamando al constructor de serialización y <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método de la clase base.

 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Marcar todos los campos no serializables](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)