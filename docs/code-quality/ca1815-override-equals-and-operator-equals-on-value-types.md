---
title: "CA1815: Reemplazar Equals y el operador Equals en los tipos de valor | Microsoft Docs"
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
  - "CA1815"
  - "OverrideEqualsAndOperatorEqualsOnValueTypes"
helpviewer_keywords: 
  - "OverrideEqualsAndOperatorEqualsOnValueTypes"
  - "CA1815"
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1815: Reemplazar Equals y el operador Equals en los tipos de valor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|Identificador de comprobación|CA1815|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo de valor público no reemplaza <xref:System.Object.Equals%2A?displayProperty=fullName> ni implementa al operador de igualdad \(\=\=\).  Esta regla no comprueba las enumeraciones.  
  
## Descripción de la regla  
 Para los tipos de valor, la implementación heredada de <xref:System.Object.Equals%2A> utiliza la biblioteca de reflexiones y compara el contenido de todos los campos.  Mediante el cálculo, la reflexión es cara y no es necesario comparar cada campo para comprobar si hay igualdad.  Si espera que los usuarios comparen u ordenen las instancias, o las utiliza como claves de tabla hash, el tipo de valor debería implementar <xref:System.Object.Equals%2A>.  Si su lenguaje de programación admite la sobrecarga de operadores, también debería proporcionar una implementación de la igualdad y operadores de desigualdad.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, proporcione una implementación de <xref:System.Object.Equals%2A>.  Si puede, implemente al operador de igualdad.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si las instancias del tipo de valor no se comparan entre sí.  
  
## Ejemplo de infracción  
  
### Descripción  
 En el siguiente ejemplo se muestra una estructura \(tipo de valor\) que infringe esta regla.  
  
### Código  
 [!code-cs[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## Ejemplo de cómo corregir  
  
### Descripción  
 En el ejemplo siguiente se invalida <xref:System.ValueType.Equals%2A?displayProperty=fullName> y se implementan los operadores de igualdad \(\=\=, \!\=\) para corregir la infracción anterior.  
  
### Código  
 [!code-cs[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## Reglas relacionadas  
 [CA2224: Reemplazar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Sobrecargar el operador de igualdad al reemplazar el tipo de valor de igualdad](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## Vea también  
 <xref:System.Object.Equals%2A?displayProperty=fullName>