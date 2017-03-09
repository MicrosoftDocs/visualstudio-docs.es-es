---
title: "La instrucci&#243;n &#39;Throw&#39; no puede omitir el operando fuera de una instrucci&#243;n &#39;Catch&#39; o dentro de una instrucci&#243;n &#39;Finally&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30666"
  - "bc30666"
helpviewer_keywords: 
  - "BC30666"
ms.assetid: a208a6ea-0e36-4bf1-8984-4de1a0e38a2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;Throw&#39; no puede omitir el operando fuera de una instrucci&#243;n &#39;Catch&#39; o dentro de una instrucci&#243;n &#39;Finally&#39;
Las instrucciones `Throw` fuera de una instrucción `Catch` deben facilitar el nombre de un objeto de excepción.  
  
 **Id. de error:** BC30666  
  
### Para corregir este error  
  
1.  Especifique el nombre de un objeto de excepción que derive de `System.Exception`.  
  
2.  Reestructure el código para que la instrucción `Throw` se encuentre dentro de un bloque `Catch`.  
  
## Vea también  
 [Throw \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/throw-statement)   
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Clase de excepción en Visual Basic](http://msdn.microsoft.com/es-es/9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Control de excepciones y errores en Visual Basic](http://msdn.microsoft.com/es-es/3e351e73-cf23-40ab-8b60-05794160529e)