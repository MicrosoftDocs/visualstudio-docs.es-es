---
title: 'CA2229: Implementar constructores de serialización | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ea0aeb5e1a493d49c1b5fa6db4fbce8f0ad8ea71
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591248"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementar constructores de serialización
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA2229: implementar constructores de serialización](https://docs.microsoft.com/visualstudio/code-quality/ca2229-implement-serialization-constructors).

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|Identificador de comprobación|CA2229|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 El tipo implementa la <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> interfaz, no es un delegado o interfaz y una de las siguientes condiciones es verdadera:

-   El tipo no tiene un constructor que toma un <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objeto y un <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> objeto (la firma del constructor de serialización).

-   El tipo está sellado y el modificador de acceso de su constructor de serialización no está protegida (familia).

-   El tipo está sellado y el modificador de acceso de su constructor de serialización no es privado.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla es relevante para los tipos que admiten la serialización personalizada. Un tipo admite la serialización personalizada si implementa el <xref:System.Runtime.Serialization.ISerializable> interfaz. Se requiere el constructor de serialización para deserializar o volver a crear los objetos que se han serializado utilizando el <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, implemente el constructor de serialización. Para una clase sellada, marque el constructor como privado; de lo contrario, márquelo como protegido.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una infracción de la regla. El tipo no será deserializable y no funcionará en muchos escenarios.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que cumple la regla.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Vea también
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>



