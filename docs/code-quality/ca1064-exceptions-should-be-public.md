---
title: "CA1064: Las excepciones deben ser p&#250;blicas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1064"
  - "ExceptionsShouldBePublic"
helpviewer_keywords: 
  - "CA1064"
  - "ExceptionsShouldBePublic"
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1064: Las excepciones deben ser p&#250;blicas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ExceptionsShouldBePublic|  
|Identificador de comprobación|CA1064|  
|Categoría|Microsoft.Design|  
|Cambio problemático|No|  
  
## Motivo  
 Una excepción no pública deriva directamente de <xref:System.Exception>, <xref:System.SystemException> o <xref:System.ApplicationException>.  
  
## Descripción de la regla  
 Una excepción interna sólo se ve dentro de su propio ámbito interno.  Cuando la excepción esté fuera del ámbito interno, sólo se podrá usar la excepción base para detectarla.  Si la excepción interna se hereda de <xref:System.Exception>, <xref:System.SystemException> o <xref:System.ApplicationException>, el código externo no tendrá información suficiente para saber qué hacer con ella.  
  
 Sin embargo, si el código tiene una excepción pública que después se utiliza como base para una excepción interna, es razonable suponer que el código que está fuera del ámbito podría hacer algo inteligente con la excepción base.  La excepción pública tendrá más información que T:System.Exception, T:System.SystemException o T:System.ApplicationException.  
  
## Cómo corregir infracciones  
 Haga pública la excepción o derive la excepción interna de una excepción pública que no sea <xref:System.Exception>, <xref:System.SystemException> o <xref:System.ApplicationException>.  
  
## Cuándo suprimir advertencias  
 Suprima un mensaje de esta regla si está seguro de que en todos los casos la excepción privada será detectada dentro de su propio ámbito interno.  
  
## Ejemplo  
 Esta regla se desencadena en el primer método de ejemplo, FirstCustomException, porque la clase de excepción deriva directamente de Exception y es interna.  La regla no se desencadena en la clase SecondCustomException porque aunque la clase también deriva directamente de Exception, la clase está declarada como pública.  La tercera clase tampoco desencadena la regla porque no deriva directamente de <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName> o <xref:System.ApplicationException?displayProperty=fullName>.  
  
 [!code-cs[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]