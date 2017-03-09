---
title: "&#39;&lt;method1&gt;&#39; no puede invalidar &#39;&lt;method2&gt;&#39; porque es una instrucci&#243;n &#39;Declare&#39;. | Microsoft Docs"
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
  - "vbc30474"
  - "bc30474"
helpviewer_keywords: 
  - "BC30474"
ms.assetid: 7277e8cc-aa3c-40c3-8682-c8c42d2ee921
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;method1&gt;&#39; no puede invalidar &#39;&lt;method2&gt;&#39; porque es una instrucci&#243;n &#39;Declare&#39;.
Ha intentado invalidar un delegado en el nombre de la clase base que se ha declarado con una instrucción `Declare`.  
  
 **Identificador de error:** BC30474  
  
### Para corregir este error  
  
1.  Cambie el miembro invalidado para que no sea una instrucción `Declare`.  
  
2.  No intente invalidar este método.  
  
## Vea también  
 [Declare \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/declare-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Invalidar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)