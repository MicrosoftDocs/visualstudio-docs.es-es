---
title: 'CA2229: implementar constructores de serialización | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56d53717afc8cd966903e75f77e1745de0031745
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662846"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementar constructores de serialización
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|Identificador de comprobación|CA2229|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 El tipo implementa la interfaz <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, no es un delegado o una interfaz, y se cumple una de las condiciones siguientes:

- El tipo no tiene un constructor que tome un objeto <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> y un objeto <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> (la firma del constructor de serialización).

- El tipo no está sellado y el modificador de acceso de su constructor de serialización no está protegido (familia).

- El tipo está sellado y el modificador de acceso de su constructor de serialización no es privado.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla es relevante para los tipos que admiten la serialización personalizada. Un tipo admite la serialización personalizada si implementa la interfaz <xref:System.Runtime.Serialization.ISerializable>. El constructor de serialización es necesario para deserializar o volver a crear los objetos que se han serializado mediante el método <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente el constructor de serialización. Para una clase sellada, marque el constructor como privado; de lo contrario, márquelo como protegido.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una infracción de la regla. No se puede deserializar el tipo y no funcionará en muchos escenarios.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que cumple la regla.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Vea también
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
