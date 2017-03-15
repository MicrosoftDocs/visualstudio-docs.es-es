---
title: "CA1055: Los valores devueltos URI no deben ser cadenas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1055"
  - "UriReturnValuesShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1055"
  - "UriReturnValuesShouldNotBeStrings"
ms.assetid: 40e39873-7872-4988-8195-9eb0ade9ece0
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA1055: Los valores devueltos URI no deben ser cadenas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriReturnValuesShouldNotBeStrings|  
|Identificador de comprobación|CA1055|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El nombre de un método contiene "uri", "Uri", "urna", "Urna", "url" o "Url" y el método devuelve una cadena.  
  
## Descripción de la regla  
 Esta regla divide el nombre del método en símbolos \(token\) basándose en la convención Pascal de uso de mayúsculas y, a continuación, comprueba cada símbolo para ver si son iguales a "uri", "Uri", "urn", "Urn", "url" o "Url".  Si hay una coincidencia, la regla supone que el método devuelve un identificador de recursos uniforme \(URI\).  Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad.  La clase <xref:System.Uri?displayProperty=fullName> proporciona estos servicios de una manera segura.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el tipo de valor devuelto a <xref:System.Uri>.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el valor devuelto no representa ningún URI.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo, `ErrorProne`, que infringe esta regla, y un tipo, `SaferWay`, que la cumple.  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1055-uri-return-values-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1055-uri-return-values-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1055-uri-return-values-should-not-be-strings_1.cpp)]  
  
## Reglas relacionadas  
 [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)