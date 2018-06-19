---
title: 'CA2235: Marcar todos los campos no serializables'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04a49671c4efc725a8796b050764dc4d9949f808
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922261"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Marcar todos los campos no serializables
|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|Identificador de comprobación|CA2235|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un campo de instancia de un tipo que no es serializable se declara en un tipo que es serializable.

## <a name="rule-description"></a>Descripción de la regla
 Un tipo serializable es aquel que se marca con el <xref:System.SerializableAttribute?displayProperty=fullName> atributo. Cuando se serializa el tipo, un <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> excepción se produce si un tipo contiene un campo de instancia de un tipo que no es serializable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, aplique el <xref:System.NonSerializedAttribute?displayProperty=fullName> atributo al campo que no es serializable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Sólo suprima las advertencias de esta regla si un <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> tipo se declara que permite que las instancias del campo para serializar y deserializar.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe la regla y un tipo que infringe la regla.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)