---
title: 'CA1036: Reemplazar métodos en tipos comparables | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d5e366144a70e25fc805d63ddcc7664a60df4303
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Reemplazar métodos en tipos comparables
|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|Identificador de comprobación|CA1036|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo público o protegido implementa la <xref:System.IComparable?displayProperty=fullName> de interfaz y no invalida <xref:System.Object.Equals%2A?displayProperty=fullName> o no sobrecarga el operador específico del lenguaje para la igualdad, desigualdad, menor que o mayor que. La regla no informa de una infracción si el tipo hereda solo una implementación de la interfaz.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los tipos que definen un criterio de ordenación personalizado implementan la <xref:System.IComparable> interfaz. El <xref:System.IComparable.CompareTo%2A> método devuelve un valor entero que indica el orden correcto para que dos instancias del tipo. Esta regla identifica los tipos que establecen un criterio de ordenación; Esto implica que el significado normal de igualdad, desigualdad, menor que y mayor que no se aplican. Cuando se proporciona una implementación de <xref:System.IComparable>, normalmente debe invalidar <xref:System.Object.Equals%2A> para que devuelva valores que son coherentes con <xref:System.IComparable.CompareTo%2A>. Si invalida <xref:System.Object.Equals%2A> y está codificando en un lenguaje que admite las sobrecargas de operador, también debería proporcionar operadores que son coherentes con <xref:System.Object.Equals%2A>.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, invalidar <xref:System.Object.Equals%2A>. Si su lenguaje de programación admite la sobrecarga de operadores, proporcione los operadores siguientes:  
  
-   op_Equality  
  
-   op_Inequality  
  
-   op_LessThan  
  
-   op_GreaterThan  
  
 En C#, los tokens que se usan para representar estos operadores son: ==,! =, \<, y >.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando la causan los operadores que faltan y el lenguaje de programación no admite la sobrecarga de operadores, como es el caso de Visual Basic. También es seguro suprimir una advertencia para de esta regla cuando se desencadena en los operadores de igualdad distinto op_Equality si determina que la implementación de los operadores no tienen sentido en el contexto de la aplicación. Sin embargo, siempre debería sobre op_Equality y el operador == si invalida Object.Equals.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente contiene un tipo que implementa correctamente <xref:System.IComparable>. Comentarios de código identifican los métodos que cumplen las distintas reglas que están relacionados con <xref:System.Object.Equals%2A> y <xref:System.IComparable> interfaz.  
  
 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## <a name="example"></a>Ejemplo  
 La siguiente aplicación comprueba el comportamiento de la <xref:System.IComparable> implementación que se mostró anteriormente.  
  
 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators)