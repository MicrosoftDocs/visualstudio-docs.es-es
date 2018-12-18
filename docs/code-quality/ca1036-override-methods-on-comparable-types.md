---
title: 'CA1036: Reemplazar métodos en tipos comparables'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed69ba759d63ba27114bc097ac1fd9ccbe424edd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547743"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Reemplazar métodos en tipos comparables

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|Identificador de comprobación|CA1036|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido implementa la <xref:System.IComparable?displayProperty=fullName> interfaz y no invalida <xref:System.Object.Equals%2A?displayProperty=fullName> o no sobrecarga el operador específico del lenguaje para la igualdad, desigualdad, menor: mayor o menor-que. La regla no informa de una infracción si el tipo hereda solo una implementación de la interfaz.

## <a name="rule-description"></a>Descripción de la regla

Los tipos que definen un criterio de ordenación personalizados implementan la <xref:System.IComparable> interfaz. El <xref:System.IComparable.CompareTo%2A> método devuelve un valor entero que indica el orden correcto para que dos instancias del tipo. Esta regla identifica los tipos que establezca un criterio de ordenación. Establecer un criterio de ordenación implica que el significado normal de igualdad, desigualdad, menor-que y mayor-que no son aplicables. Cuando se proporciona una implementación de <xref:System.IComparable>, normalmente debe invalidar también <xref:System.Object.Equals%2A> para que devuelva valores que sean coherentes con <xref:System.IComparable.CompareTo%2A>. Si invalida <xref:System.Object.Equals%2A> y son de codificación en un lenguaje que admite las sobrecargas de operador, también debe proporcionar los operadores que son coherentes con <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, invalidar <xref:System.Object.Equals%2A>. Si su lenguaje de programación admite la sobrecarga de operadores, proporcione los siguientes operadores:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

En C#, los tokens que se usan para representar estos operadores son los siguientes:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de regla CA1036 si se ha provocado la infracción a la falta de operadores y el lenguaje de programación no admite la sobrecarga de operadores, como sucede con Visual Basic. También es seguro suprimir una advertencia para de esta regla cuando se desencadena en los operadores de igualdad distinto op_Equality si determina que la implementación de los operadores no tiene sentido en el contexto de la aplicación. Sin embargo, siempre debería sobre op_Equality y el operador == si invalida Object.Equals.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente contiene un tipo que implementa correctamente <xref:System.IComparable>. Comentarios de código identifican los métodos que satisfacen diversas reglas que están relacionados con <xref:System.Object.Equals%2A> y <xref:System.IComparable> interfaz.

 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

## <a name="example"></a>Ejemplo
 La siguiente aplicación comprueba que el comportamiento de la <xref:System.IComparable> implementación que se mostró anteriormente.

 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators)