---
title: "CA1054: Los par&#225;metros de URI no deben ser cadenas | Microsoft Docs"
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
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
helpviewer_keywords: 
  - "CA1054"
  - "UriParametersShouldNotBeStrings"
ms.assetid: 8e99d72b-a658-47a7-8dd5-9784ce2c30b8
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1054: Los par&#225;metros de URI no deben ser cadenas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UriParametersShouldNotBeStrings|  
|Identificador de comprobación|CA1054|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo declara un método que tiene un parámetro de cadena cuyo nombre contiene "uri", "Uri", "urn", "Urn", "url" o "Url", pero el tipo no declara una sobrecarga que toma un parámetro <xref:System.Uri?displayProperty=fullName>.  
  
## Descripción de la regla  
 Esta regla divide el nombre del parámetro en símbolos \(token\) basándose en la convención Camel de uso de mayúsculas y, a continuación, comprueba cada símbolo para ver si son iguales a "uri", "Uri", "urn", "Urn", "url" o "Url".  Si hay una coincidencia, la regla supone que el parámetro representa un identificador de recursos uniforme \(URI\).  Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad.  Si un método toma una representación de cadena de un URI, debe proporcionarse la sobrecarga correspondiente que toma una instancia de la clase <xref:System.Uri> que proporciona estos servicios de forma segura.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el parámetro a un tipo <xref:System.Uri>; éste es un cambio importante.  Como alternativa, proporcione una sobrecarga del método que tome un parámetro <xref:System.Uri>; éste es un cambio poco problemático.  
  
## Cuándo suprimir advertencias  
 Puede suprimirse de forma segura una advertencia de esta regla si el parámetro no representa ningún URI.  
  
## Ejemplo  
 El ejemplo siguiente muestra un tipo, `ErrorProne`, que infringe esta regla, y un tipo, `SaferWay`, que la cumple.  
  
 [!code-cs[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CSharp/ca1054-uri-parameters-should-not-be-strings_1.cs)]
 [!code-vb[FxCop.Design.UriNotString#1](../code-quality/codesnippet/VisualBasic/ca1054-uri-parameters-should-not-be-strings_1.vb)]
 [!code-cpp[FxCop.Design.UriNotString#1](../code-quality/codesnippet/CPP/ca1054-uri-parameters-should-not-be-strings_1.cpp)]  
  
## Reglas relacionadas  
 [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)  
  
 [CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)