---
title: 'CA1046: No sobrecargar el operador equals en tipos de referencia | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 344dfe7a4e35bf42e9e0a4efb2ca9bdf1b8f5d6b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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
  
 **¿un = nueva (2,2) y b = nueva (2,2) son iguales? No**  
**¿c y a son igual? Sí**  
**¿b y a son ==? No**  
**¿c y a son ==? Sí**   
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Operadores de igualdad](/dotnet/standard/design-guidelines/equality-operators)