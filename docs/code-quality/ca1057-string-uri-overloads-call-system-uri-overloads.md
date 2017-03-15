---
title: "CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri | Microsoft Docs"
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
  - "CA1057"
  - "StringUriOverloadsCallSystemUriOverloads"
helpviewer_keywords: 
  - "StringUriOverloadsCallSystemUriOverloads"
  - "CA1057"
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1057: Las sobrecargas URI de cadena llaman a sobrecargas System.Uri
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StringUriOverloadsCallSystemUriOverloads|  
|Identificador de comprobación|CA1057|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo declara una sobrecarga de método que sólo se distingue por reemplazar un parámetro de cadena con un parámetro <xref:System.Uri?displayProperty=fullName>, y la sobrecarga que toma el parámetro de cadena no llama a la sobrecarga que toma el parámetro <xref:System.Uri>.  
  
## Descripción de la regla  
 Dado que las sobrecargas sólo se distinguen por el parámetro de cadena\/<xref:System.Uri>, se supone que la cadena representa un identificador de recursos uniforme \(URI\).  Las representaciones de cadena de identificadores URI tienen tendencia a analizar y codificar errores, por lo que pueden crear puntos vulnerables en la seguridad.  La clase <xref:System.Uri> proporciona estos servicios de una manera segura.  Para aprovechar las ventajas de la clase <xref:System.Uri>, la sobrecarga de la cadena debería llamar a la sobrecarga de <xref:System.Uri> utilizando el argumento de cadena.  
  
## Cómo corregir infracciones  
 Vuelva a implementar el método que utiliza la representación de cadena del URI para crear una instancia de la clase <xref:System.Uri> utilizando el argumento de cadena y, a continuación, pasa el objeto <xref:System.Uri> a la sobrecarga que tiene el parámetro <xref:System.Uri>.  
  
## Cuándo suprimir advertencias  
 Puede suprimirse de forma segura una advertencia de esta regla si el parámetro de cadena no representa ningún URI.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra una sobrecarga de cadena correctamente implementada.  
  
 [!code-cs[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]  
  
## Reglas relacionadas  
 [CA2234: Pase objetos System.Uri en lugar de cadenas](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)  
  
 [CA1056: Las propiedades URI no deben ser cadenas](../code-quality/ca1056-uri-properties-should-not-be-strings.md)  
  
 [CA1054: Los parámetros de URI no deben ser cadenas](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)  
  
 [CA1055: Los valores devueltos URI no deben ser cadenas](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)