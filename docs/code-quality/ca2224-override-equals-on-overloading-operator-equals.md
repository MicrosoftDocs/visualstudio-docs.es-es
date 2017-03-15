---
title: "CA2224: Reemplazar Equals al sobrecargar operadores de igualdad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
  - "OverrideEqualsOnOverridingOperatorEquals"
helpviewer_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2224: Reemplazar Equals al sobrecargar operadores de igualdad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|  
|Identificador de comprobación|CA2224|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo público implementa el operador de igualdad, pero no reemplaza <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## Descripción de la regla  
 El operador de igualdad está pensado para que desde un punto de vista sintáctico sea un medio práctico de tener acceso a la funcionalidad del método <xref:System.Object.Equals%2A>.  Si implementa el operador de igualdad, su lógica debe ser idéntica a la de <xref:System.Object.Equals%2A>.  
  
 El compilador de C\# emite una advertencia si su código infringe esta regla.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, debe quitar la implementación del operador de igualdad o reemplazar <xref:System.Object.Equals%2A>, y que los dos métodos devuelvan los mismos valores.  Si el operador de igualdad no produce un comportamiento incoherente, puede corregir la infracción proporcionando una implementación de <xref:System.Object.Equals%2A> que llame al método <xref:System.Object.Equals%2A> de la clase base.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el operador de igualdad devuelve el mismo valor que la implementación heredada de <xref:System.Object.Equals%2A>.  La sección Ejemplo incluye un tipo que puede suprimir una advertencia de esta regla sin ningún riesgo.  
  
## Ejemplos de definiciones de igualdad incoherentes  
  
### Descripción  
 En el siguiente ejemplo se muestra un tipo con definiciones incoherentes de igualdad.  `BadPoint` modifica el significado de igualdad proporcionando una implementación personalizada del operador de igualdad, pero no reemplaza <xref:System.Object.Equals%2A> de modo que su comportamiento es idéntico.  
  
### Código  
 [!code-cs[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## Ejemplo  
 El código siguiente comprueba el comportamiento de `BadPoint`.  
  
 [!code-cs[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **¿a \= \(\[0\] 1,1\) y b \= \(\[1\] 2,2\) son iguales?  No**  
**a \=\= b ?  No**  
**¿a1 y a son iguales?  Sí**  
**¿a1 \=\= a?  Sí**  
**¿b y bcopy son iguales?  No**  
**¿b \=\= bcopy?  Sí**    
## Ejemplo  
 El ejemplo siguiente muestra un tipo que técnicamente infringe esta regla, pero no se comporta de forma incoherente.  
  
 [!code-cs[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## Ejemplo  
 El código siguiente comprueba el comportamiento de `GoodPoint`.  
  
 [!code-cs[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **¿a \= \(1,1\) y b \= \(2,2\) son iguales?  No**  
**a \=\= b ?  No**  
**¿a1 y a son iguales?  Sí**  
**¿a1 \=\= a?  Sí**  
**¿b y bcopy son iguales?  Sí**  
**¿b \=\= bcopy?  Sí**    
## Ejemplo de clase  
  
### Descripción  
 En el siguiente ejemplo se muestra una clase \(tipo de referencia\) que infringe esta regla.  
  
### Código  
 [!code-cs[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## Ejemplo  
 El ejemplo siguiente corrige la infracción invalidando <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## Ejemplo de estructura  
  
### Descripción  
 En el siguiente ejemplo se muestra una estructura \(tipo de valor\) que infringe esta regla.  
  
### Código  
 [!code-cs[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## Ejemplo  
 El ejemplo siguiente corrige la infracción invalidando <xref:System.ValueType.Equals%2A?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## Reglas relacionadas  
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218: Reemplazar el método GetHashCode al reemplazar el método Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Sobrecargar el operador de igualdad al reemplazar el tipo de valor de igualdad](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)