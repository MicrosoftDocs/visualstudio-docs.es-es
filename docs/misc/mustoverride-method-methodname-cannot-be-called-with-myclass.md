---
title: "No se puede llamar al m&#233;todo &#39;MustOverride&#39; &#39;&lt;nombreM&#233;todo&gt;&#39; con &#39;MyClass&#39;. | Microsoft Docs"
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
  - "bc30614"
  - "vbc30614"
helpviewer_keywords: 
  - "BC30614"
ms.assetid: fc57af41-1552-46d1-9727-341f1835e661
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede llamar al m&#233;todo &#39;MustOverride&#39; &#39;&lt;nombreM&#233;todo&gt;&#39; con &#39;MyClass&#39;.
`MyClass` es equivalente a `Me`, pero todas las invocaciones de método que contiene se tratan como si el método invocado fuera `NotOverridable`.  
  
 **Identificador de error:** BC30614  
  
### Para corregir este error  
  
-   Quite el modificador `MustOverride`, o declare el método en una clase base y herede y reemplace esa clase.  
  
## Vea también  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)