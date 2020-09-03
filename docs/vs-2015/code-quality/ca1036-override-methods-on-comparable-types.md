---
title: 'CA1036: invalidar métodos en tipos comparables | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52247c9175b22d3d96aa91557ee133f37c55e789
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546606"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Invalidar métodos en tipos comparables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|Identificador de comprobación|CA1036|
|Category|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un tipo público o protegido implementa la <xref:System.IComparable?displayProperty=fullName> interfaz y no invalida o no <xref:System.Object.Equals%2A?displayProperty=fullName> sobrecarga el operador específico del lenguaje para la igualdad, desigualdad, menor que o mayor que. La regla no notifica una infracción si el tipo hereda solo una implementación de la interfaz.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos que definen un criterio de ordenación personalizado implementan la <xref:System.IComparable> interfaz. El <xref:System.IComparable.CompareTo%2A> método devuelve un valor entero que indica el criterio de ordenación correcto para dos instancias del tipo. Esta regla identifica los tipos que establecen un criterio de ordenación; Esto implica que no se aplica el significado ordinario de igualdad, desigualdad, menor que y mayor que. Cuando se proporciona una implementación de <xref:System.IComparable> , normalmente también se debe invalidar <xref:System.Object.Equals%2A> para que devuelva valores que sean coherentes con <xref:System.IComparable.CompareTo%2A> . Si invalida <xref:System.Object.Equals%2A> y está codificando en un lenguaje que admite sobrecargas de operador, también debe proporcionar operadores coherentes con <xref:System.Object.Equals%2A> .

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, invalide <xref:System.Object.Equals%2A> . Si el lenguaje de programación admite la sobrecarga de operadores, proporcione los operadores siguientes:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  En C#, los tokens que se usan para representar estos operadores son los siguientes: = =,! =, \<, and > .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando la infracción está causada por operadores que faltan y el lenguaje de programación no admite la sobrecarga de operadores, como es el caso de Visual Basic .NET. También es seguro suprimir una advertencia de esta regla cuando se activa en operadores de igualdad distintos de op_Equality si determina que la implementación de los operadores no tiene sentido en el contexto de la aplicación. Sin embargo, siempre debe sobrepasar op_Equality y el operador = = si invalida Object. Equals.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente contiene un tipo que implementa correctamente <xref:System.IComparable> . Los comentarios de código identifican los métodos que cumplen varias reglas que están relacionadas con <xref:System.Object.Equals%2A> y la <xref:System.IComparable> interfaz.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Ejemplo
 La siguiente aplicación comprueba el comportamiento de la <xref:System.IComparable> implementación que se mostró anteriormente.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Consulte también
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [Operadores de igualdad](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
