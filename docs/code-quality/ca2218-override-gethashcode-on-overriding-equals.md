---
title: "CA2218: Reemplazar el m&#233;todo GetHashCode al reemplazar el m&#233;todo Equals | Microsoft Docs"
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
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
helpviewer_keywords: 
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2218: Reemplazar el m&#233;todo GetHashCode al reemplazar el m&#233;todo Equals
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideGetHashCodeOnOverridingEquals|  
|Identificador de comprobación|CA2218|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un tipo público reemplaza <xref:System.Object.Equals%2A?displayProperty=fullName> pero no reemplaza <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.  
  
## Descripción de la regla  
 <xref:System.Object.GetHashCode%2A> devuelve un valor basado en la instancia actual que se adapta para los algoritmos hash y a las estructuras de datos como una tabla hash.  Dos objetos iguales y que son el mismo tipo deben devolver el mismo código hash para garantizar que las instancias de los tipos siguientes funcionan correctamente.  
  
-   <xref:System.Collections.HashTable?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Dictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortList?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.HybredDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>  
  
-   Tipos que implementan <xref:System.Collections.Generic.IEqualityComparer?displayProperty=fullName>  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, proporcione una implementación de <xref:System.Object.GetHashCode%2A>.  Para obtener un par de objetos del mismo tipo, debe asegurarse de que la implementación devuelve el mismo valor si la implementación de <xref:System.Object.Equals%2A> devuelve `true` para el par.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo de clase  
  
### Descripción  
 En el siguiente ejemplo se muestra una clase \(tipo de referencia\) que infringe esta regla.  
  
### Código  
 [!code-cs[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]  
  
### Comentarios  
 El ejemplo siguiente corrige la infracción invalidando <xref:System.Object.GetHashCode>.  
  
### Código  
 [!code-cs[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]  
  
## Ejemplo de estructura  
  
### Descripción  
 En el siguiente ejemplo se muestra una estructura \(tipo de valor\) que infringe esta regla.  
  
### Código  
 [!code-cs[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]  
  
### Comentarios  
 El ejemplo siguiente corrige la infracción invalidando <xref:System.Object.GetHashCode>.  
  
### Código  
 [!code-cs[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]  
  
## Reglas relacionadas  
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Las sobrecargas del operador tienen alternativas con nombre](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Reemplazar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Sobrecargar el operador de igualdad al reemplazar el tipo de valor de igualdad](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
## Vea también  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Collections.HashTable?displayProperty=fullName>   
 [Operadores de igualdad](../Topic/Equality%20Operators.md)