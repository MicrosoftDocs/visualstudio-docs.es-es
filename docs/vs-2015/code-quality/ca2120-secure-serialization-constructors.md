---
title: 'CA2120: constructores de serialización seguros | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 10cfa03adb74871fb42a6e1c2ce4ab4ba6bcae75
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544344"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Proteger los constructores de serializaciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|SecureSerializationConstructors|
|Identificador de comprobación|CA2120|
|Category|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 El tipo implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz, no es un delegado o una interfaz y se declara en un ensamblado que permite llamadores parcialmente confiables. El tipo tiene un constructor que toma un <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objeto y un <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> objeto (la firma del constructor de serialización). Este constructor no está protegido por una comprobación de seguridad, pero uno o varios de los constructores normales del tipo están protegidos.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla es relevante para los tipos que admiten la serialización personalizada. Un tipo admite la serialización personalizada si implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz. El constructor de serialización es necesario y se utiliza para deserializar o volver a crear los objetos que se han serializado mediante el <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método. Dado que el constructor de serialización asigna e inicializa objetos, las comprobaciones de seguridad que se encuentran en constructores normales también deben estar presentes en el constructor de serialización. Si infringe esta regla, los llamadores que no puedan crear una instancia podrían usar el constructor de serialización para hacerlo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, proteja el constructor de serialización con demandas de seguridad idénticas a las que protegen a otros constructores.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una infracción de la regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe la regla.

 [!code-csharp[FxCop.Security.SerialCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SerialCtors/cs/FxCop.Security.SerialCtors.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Consulte también
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
