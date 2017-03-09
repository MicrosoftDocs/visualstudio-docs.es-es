---
title: "CA1046: No sobrecargar el operador de igualdad en los tipos de referencia | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
  - "CA1046"
helpviewer_keywords: 
  - "CA1046"
  - "DoNotOverrideOperatorEqualsOnReferenceTypes"
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1046: No sobrecargar el operador de igualdad en los tipos de referencia
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|Identificador de comprobación|CA1046|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo de referencia público o anidado público sobrecarga el operador de igualdad.  
  
## Descripción de la regla  
 Para los tipos de referencia, la implementación predeterminada del operador de igualdad casi siempre es correcta.  De manera predeterminada, dos referencias son iguales sólo si señalan al mismo objeto.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite la implementación del operador de igualdad.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando el tipo de referencia se comporte como tipo de valor integrado.  Si tiene sentido realizar sumas o restas en instancias del tipo, es probable que sea correcto implementar el operador de igualdad y suprimir la infracción.  
  
## Ejemplo  
 El ejemplo siguiente muestra el comportamiento predeterminado al comparar dos referencias.  
  
 [!code-cs[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## Ejemplo  
 La aplicación siguiente compara algunas referencias.  
  
 [!code-cs[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **¿a \= nuevo \(2,2\) y b \= nuevo \(2,2\) son iguales?  No**  
**¿c y a son iguales?  Sí**  
**b y a son \=\= ?  No**  
**c y a son \=\= ?  Sí**    
## Reglas relacionadas  
 [CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## Vea también  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Operadores de igualdad](../Topic/Equality%20Operators.md)