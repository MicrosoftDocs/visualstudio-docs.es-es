---
title: 'CA2235: marcar todos los campos no serializables | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 709bc3dea92752d9e18c3163fe43864f5896471c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666775"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Marcar todos los campos no serializables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|Identificador de comprobación|CA2235|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un campo de instancia de un tipo que no es serializable se declara en un tipo que es serializable.

## <a name="rule-description"></a>Descripción de la regla
 Un tipo serializable es el que está marcado con el atributo <xref:System.SerializableAttribute?displayProperty=fullName>. Cuando se serializa el tipo, se produce una excepción <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> si un tipo contiene un campo de instancia de un tipo que no es serializable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, aplique el atributo <xref:System.NonSerializedAttribute?displayProperty=fullName> al campo que no es serializable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Solo se debe suprimir una advertencia de esta regla si se declara un tipo <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> que permita la serialización y deserialización de las instancias del campo.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe la regla y un tipo que cumple la regla.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2236: Llamar a métodos de clase base en tipos ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementar ISerializable correctamente](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementar métodos de serialización correctamente](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Proporcionar métodos de deserialización para campos opcionales](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Proteger los constructores de serializaciones](../code-quality/ca2120-secure-serialization-constructors.md)
