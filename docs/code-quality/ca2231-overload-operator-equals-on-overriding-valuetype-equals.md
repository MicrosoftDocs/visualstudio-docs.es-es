---
title: "CA2231: Sobrecargar el operador de igualdad al reemplazar el tipo de valor de igualdad | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
  - "CA2231"
  - "OverrideOperatorEqualsOnOverridingValueTypeEquals"
helpviewer_keywords: 
  - "CA2231"
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2231: Sobrecargar el operador de igualdad al reemplazar el tipo de valor de igualdad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|Identificador de comprobación|CA2231|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo de valor reemplaza <xref:System.Object.Equals%2A?displayProperty=fullName> pero no implementa al operador de igualdad.  
  
## Descripción de la regla  
 En la mayoría de los lenguajes de programación no hay una implementación predeterminada del operador de igualdad \(\=\=\) para tipos de valor.  Si su lenguaje de programación admite las sobrecargas de operador, debería considerar implementar el operador de igualdad.  Su comportamiento debería ser idéntico al de <xref:System.Object.Equals%2A>.  
  
 No puede utilizar el operador de igualdad predeterminado en una implementación sobrecargada del operador de igualdad.  Con ello se producirá un desbordamiento de pila.  Para implementar el operador de igualdad, utilice el método Object.Equals en la implementación.  Por ejemplo:  
  
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
 Para corregir una infracción de esta regla, implemente el operador de igualdad.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla; sin embargo, se recomienda proporcionar el operador de igualdad, si es posible.  
  
## Ejemplo  
 El siguiente ejemplo se define un tipo que infringe esta regla.  
  
 [!code-cs[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]  
  
## Reglas relacionadas  
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Reemplazar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: Reemplazar el método GetHashCode al reemplazar el método Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## Vea también  
 <xref:System.Object.Equals%2A?displayProperty=fullName>