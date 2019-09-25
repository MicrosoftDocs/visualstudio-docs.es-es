---
title: 'CA2120: Proteger los constructores de serializaciones'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38de3597d3693b072fec12f64211af4469851627
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232539"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Proteger los constructores de serializaciones

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|Identificador de comprobación|CA2120|
|Categoría|Microsoft.Security|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
El tipo implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz, no es un delegado o una interfaz y se declara en un ensamblado que permite llamadores parcialmente confiables. El tipo tiene un constructor que toma un <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objeto y un <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> objeto (la firma del constructor de serialización). Este constructor no está protegido por una comprobación de seguridad, pero uno o varios de los constructores normales del tipo están protegidos.

## <a name="rule-description"></a>Descripción de la regla
Esta regla es relevante para los tipos que admiten la serialización personalizada. Un tipo admite la serialización personalizada si implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz. El constructor de serialización es necesario y se utiliza para deserializar o volver a crear los objetos que se han serializado mediante <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> el método. Dado que el constructor de serialización asigna e inicializa objetos, las comprobaciones de seguridad que se encuentran en constructores normales también deben estar presentes en el constructor de serialización. Si infringe esta regla, los llamadores que no puedan crear una instancia podrían usar el constructor de serialización para hacerlo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, proteja el constructor de serialización con demandas de seguridad idénticas a las que protegen a otros constructores.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima una infracción de la regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe la regla.

[!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA2229: implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2237: Marcar tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Vea también

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>