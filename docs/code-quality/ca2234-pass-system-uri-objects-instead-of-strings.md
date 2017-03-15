---
title: "CA2234: Pase objetos System.Uri en lugar de cadenas | Microsoft Docs"
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
  - "PassSystemUriObjectsInsteadOfStrings"
  - "CA2234"
helpviewer_keywords: 
  - "CA2234"
  - "PassSystemUriObjectsInsteadOfStrings"
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2234: Pase objetos System.Uri en lugar de cadenas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PassSystemUriObjectsInsteadOfStrings|  
|Identificador de comprobación|CA2234|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Se ha realizado una llamada a un método que tiene un parámetro de cadena cuyo nombre contiene "uri", "Uri", "urn", "Urn", "url", o "Url"; y el tipo del método que se declara contiene una sobrecarga del método correspondiente que tiene un parámetro <xref:System.Uri?displayProperty=fullName>.  
  
## Descripción de la regla  
 Un nombre de parámetro se divide en símbolos \(token\) basándose en la convención Camel de uso de mayúsculas y, a continuación, se comprueba cada símbolo para ver si son iguales a "uri", "Uri", "urn", "Urn", "url", o "Url".  Si hay alguna coincidencia, se supone que el parámetro representa un identificador de recursos uniforme \(URI\).  Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad.  La clase <xref:System.Uri> proporciona estos servicios de una manera segura.  Cuando hay que elegir entre dos sobrecargas que difieren sólo en la representación de un identificador URI, el usuario debería elegir la sobrecarga que toma un argumento <xref:System.Uri>.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, llame a la sobrecarga que toma el argumento el <xref:System.Uri>.  
  
## Cuándo suprimir advertencias  
 Puede suprimirse de forma segura una advertencia de esta regla si el parámetro de cadena no representa ningún URI.  
  
## Ejemplo  
 El ejemplo siguiente muestra un método, `ErrorProne`, que infringe la regla y un método, `SaferWay`, que llama correctamente al <xref:System.Uri> sobrecargado.  
  
 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-cs[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]  
  
## Reglas relacionadas  
 [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)  
  
 [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)