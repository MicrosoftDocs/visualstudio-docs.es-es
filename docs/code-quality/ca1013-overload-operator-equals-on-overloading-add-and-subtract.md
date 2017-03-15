---
title: "CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga | Microsoft Docs"
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
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
helpviewer_keywords: 
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1013: El operador de sobrecarga es igual que la suma y resta de sobrecarga
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|Identificador de comprobación|CA1013|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo público o protegido implementa los operadores de suma o resta sin implementar el operador de igualdad.  
  
## Descripción de la regla  
 Cuando las instancias de un tipo se combinan utilizando estos operadores de suma o resta, casi siempre se debe definir la igualdad para devolver `true` para cualquiera de las dos instancias que tienen los mismo valores constituyentes.  
  
 No puede utilizar el operador de igualdad predeterminado en una implementación sobrecargada del operador de igualdad.  Con ello se producirá un desbordamiento de pila.  Para implementar el operador de igualdad, utilice el método Object.Equals en la implementación.  Vea el ejemplo siguiente.  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```c#  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente al operador de igualdad para que sea matemáticamente coherente con los operadores de suma y resta.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando la implementación predeterminada del operador de igualdad proporciona el comportamiento adecuado para el tipo.  
  
## Ejemplo  
 El siguiente ejemplo se define un tipo \(`BadAddableType`\) que infringe esta regla.  Este tipo debe implementar el operador de igualdad para que al comparar los mismos campos de dos instancias cualesquiera devuelva `true` cuando los valores sean iguales.  El tipo `GoodAddableType` muestra la implementación correcta.  Observe que este tipo también implementa al operador de desigualdad y reemplaza <xref:System.Object.Equals%2A> para cumplir otras reglas.  Una implementación completa también implementaría <xref:System.Object.GetHashCode%2A>.  
  
 [!code-cs[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## Ejemplo  
 En el siguiente ejemplo se comprueba la igualdad utilizando instancias de los tipos definidos anteriormente en este tema para mostrar el comportamiento correcto y el comportamiento predeterminado del operador de igualdad.  
  
 [!code-cs[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Tipo no válido: ¿{2,2} {2,2} son iguales?  No**  
**Buen tipo: ¿{3,3} {3,3} son iguales?  Sí**  
**Buen tipo: ¿{3,3} {3,3} son \=\=?   Sí**  
**Tipo no válido: ¿{2,2} {9,9} son iguales?  No**  
**Buen tipo: ¿{3,3} {9,9} son \=\=?   No**    
## Vea también  
 [Operadores de igualdad](../Topic/Equality%20Operators.md)