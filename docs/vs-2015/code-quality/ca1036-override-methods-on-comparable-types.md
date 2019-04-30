---
title: 'CA1036: Invalidar métodos en tipos comparables | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 127bb322a9dd5c841f71a5da49b0d9a6fceaf5e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559885"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Invalidar métodos en tipos comparables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|Identificador de comprobación|CA1036|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido implementa la <xref:System.IComparable?displayProperty=fullName> interfaz y no invalida <xref:System.Object.Equals%2A?displayProperty=fullName> o no sobrecarga el operador específico del lenguaje para la igualdad, desigualdad, menor o mayor que. La regla no informa de una infracción si el tipo hereda solo una implementación de la interfaz.

## <a name="rule-description"></a>Descripción de la regla
 Los tipos que definen un criterio de ordenación personalizados implementan la <xref:System.IComparable> interfaz. El <xref:System.IComparable.CompareTo%2A> método devuelve un valor entero que indica el orden correcto para que dos instancias del tipo. Esta regla identifica los tipos que establecer un orden. Esto implica que el significado normal de igualdad, desigualdad, menor que y mayor que no son aplicables. Cuando se proporciona una implementación de <xref:System.IComparable>, normalmente debe invalidar también <xref:System.Object.Equals%2A> para que devuelva valores que sean coherentes con <xref:System.IComparable.CompareTo%2A>. Si invalida <xref:System.Object.Equals%2A> y son de codificación en un lenguaje que admite las sobrecargas de operador, también debe proporcionar los operadores que son coherentes con <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, invalidar <xref:System.Object.Equals%2A>. Si su lenguaje de programación admite la sobrecarga de operadores, proporcione los siguientes operadores:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  En C#, los tokens que se usan para representar estos operadores son como sigue: ==,! =, \<, y >.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando se produjo la infracción de operadores que faltan y el lenguaje de programación no admite la sobrecarga de operadores, como sucede con Visual Basic. NET. También es seguro suprimir una advertencia para de esta regla cuando se desencadena en los operadores de igualdad distinto op_Equality si determina que la implementación de los operadores no tiene sentido en el contexto de la aplicación. Sin embargo, siempre debería sobre op_Equality y el operador == si invalida Object.Equals.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente contiene un tipo que implementa correctamente <xref:System.IComparable>. Comentarios de código identifican los métodos que satisfacen diversas reglas que están relacionados con <xref:System.Object.Equals%2A> y <xref:System.IComparable> interfaz.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Ejemplo
 La siguiente aplicación comprueba que el comportamiento de la <xref:System.IComparable> implementación que se mostró anteriormente.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Vea también
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [Operadores de igualdad](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
