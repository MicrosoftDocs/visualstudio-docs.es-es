---
title: 'CA1046: No sobrecargar el operador de igualdad en los tipos de referencia'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6809534d14b58d60759133e972b5220fcfd58d61
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: No sobrecargar el operador de igualdad en los tipos de referencia
|||
|-|-|
|TypeName|DoNotOverrideOperatorEqualsOnReferenceTypes|
|Identificador de comprobación|CA1046|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo de referencia público o público anidado sobrecarga el operador de igualdad.

## <a name="rule-description"></a>Descripción de la regla
 Para los tipos de referencia, la implementación predeterminada del operador de igualdad casi siempre es correcta. De manera predeterminada, dos referencias son iguales sólo si señalan al mismo objeto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite la implementación del operador de igualdad.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla cuando el tipo de referencia se comporta como un tipo de valor integrado. Si tiene sentido realizar sumas o restas en instancias del tipo, es probablemente sean correcto implementar el operador de igualdad y suprimir la infracción.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra el comportamiento predeterminado al comparar dos referencias.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>Ejemplo
 La aplicación siguiente compara algunas referencias.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

 Este ejemplo produce el siguiente resultado:

 **¿un = nueva (2,2) y b = nueva (2,2) son iguales? ¿Ya no**
**c y a son igual? ¿Sí**
**b y a son ==? ¿Ya no**
**c y a son ==? Sí**
## <a name="related-rules"></a>Reglas relacionadas
 [CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Vea también
 <xref:System.Object.Equals%2A?displayProperty=fullName> [Operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators)