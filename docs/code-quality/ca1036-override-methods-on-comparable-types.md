---
title: "CA1036: Reemplazar m&#233;todos en tipos comparables | Microsoft Docs"
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
  - "CA1036"
  - "OverrideMethodsOnComparableTypes"
helpviewer_keywords: 
  - "OverrideMethodsOnComparableTypes"
  - "CA1036"
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1036: Reemplazar m&#233;todos en tipos comparables
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|Identificador de comprobación|CA1036|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo público o protegido implementa la interfaz <xref:System.IComparable?displayProperty=fullName> y no reemplaza <xref:System.Object.Equals%2A?displayProperty=fullName> ni sobrecarga el operador específico del leguaje por uno de igualdad, desigualdad o mayor que él.  La regla no informa de una infracción si el tipo hereda únicamente una implementación de la interfaz.  
  
## Descripción de la regla  
 Los tipos que definen un criterio de ordenación personalizado implementan la interfaz <xref:System.IComparable>.  El método <xref:System.IComparable.CompareTo%2A> devuelve un valor entero que indica el criterio de ordenación correcto para dos instancias del tipo.  Esta regla identifica los tipos que establecen el criterio de ordenación; esto implica que no se aplique el criterio ordinario de igualdad, desigualdad, menor o mayor que.  Cuando proporcione una implementación de <xref:System.IComparable>, normalmente también debe reemplazar <xref:System.Object.Equals%2A> de modo que devuelva los valores coherentes con <xref:System.IComparable.CompareTo%2A>.  Si reemplaza <xref:System.Object.Equals%2A> y está codificando en un lenguaje que admite las sobrecargas de operador, también debería proporcionar operadores coherentes con <xref:System.Object.Equals%2A>.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace <xref:System.Object.Equals%2A>.  Si su lenguaje de programación admite la sobrecarga de operadores, proporcione los operadores siguientes:  
  
-   op\_Equality  
  
-   op\_Inequality  
  
-   op\_LessThan  
  
-   op\_GreaterThan  
  
 En C\#, los tokens que se utilizan para representar estos operadores son los siguientes: ¡\=\=\! \= \<, y \>.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla cuando la causan los operadores que faltan y el lenguaje de programación no admite la sobrecarga de operadores, como es el caso de Visual Basic .NET.  También es seguro suprimir una advertencia de esta regla cuando se desencadena en operadores de igualdad distintos de op\_Equality si determina que no tiene sentido implementar los operadores en su contexto de aplicación.  Sin embargo, siempre debe invalidar op\_Equality y el operador \=\= si invalida Object.Equals.  
  
## Ejemplo  
 El ejemplo siguiente contiene un tipo que implementa <xref:System.IComparable> correctamente.  ‎Los comentarios de código identifican los métodos que cumplen las distintas reglas relacionadas con <xref:System.Object.Equals%2A> y la interfaz <xref:System.IComparable>.  
  
 [!code-cs[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## Ejemplo  
 La aplicación siguiente prueba el comportamiento de la implementación <xref:System.IComparable> mostrado anteriormente.  
  
 [!code-cs[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## Vea también  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Operadores de igualdad](../Topic/Equality%20Operators.md)