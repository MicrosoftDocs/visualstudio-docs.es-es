---
title: 'CA2229: Implementar constructores de serialización'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dac8a9201e375877c1b586bd6415dd81764f5d2b
ms.sourcegitcommit: dae5dfd626277b58ebd7b21a75757f683f1eacc5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739234"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementar constructores de serialización

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|Identificador de comprobación|CA2229|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
El tipo implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz, no es un delegado o una interfaz, y una de las siguientes condiciones es verdadera:

- El tipo no tiene un constructor que tome un <xref:System.Runtime.Serialization.SerializationInfo> objeto y un <xref:System.Runtime.Serialization.StreamingContext> objeto (la firma del constructor de serialización).

- El tipo no está sellado y el modificador de acceso de su constructor de serialización no está protegido (familia).

- El tipo está sellado y el modificador de acceso de su constructor de serialización no es privado.

## <a name="rule-description"></a>Descripción de la regla

Esta regla es relevante para los tipos que admiten la serialización personalizada. Un tipo admite la serialización personalizada si implementa la <xref:System.Runtime.Serialization.ISerializable> interfaz. El constructor de serialización es necesario para deserializar o volver a crear objetos que se han serializado mediante el <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, implemente el constructor de serialización. Para una clase sellada, marque el constructor como privado; de lo contrario, márquelo como protegido.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima una infracción de la regla. No se puede deserializar el tipo y no funcionará en muchos escenarios.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un tipo que cumple la regla.

[!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas

[CA2237: Marcar tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Vea también

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
