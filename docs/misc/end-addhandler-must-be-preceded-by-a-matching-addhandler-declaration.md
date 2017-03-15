---
title: "&#39;End AddHandler&#39; debe precederse de la declaraci&#243;n &#39;AddHandler&#39; correspondiente | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31124"
  - "vbc31124"
helpviewer_keywords: 
  - "BC31124"
ms.assetid: c667fecb-163a-49ca-b416-e1070f4fab1d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End AddHandler&#39; debe precederse de la declaraci&#243;n &#39;AddHandler&#39; correspondiente
Se produjo una instrucción `End AddHandler` sin una instrucción `AddHandler` correspondiente. La palabra clave `End AddHandler` debe ir precedida de una instrucción `AddHandler` correspondiente.  
  
 **Id. de error:** BC31124  
  
### Para corregir este error  
  
-   Compruebe que una instrucción `AddHandler` anterior es válida y está escrita correctamente.  
  
## Vea también  
 [AddHandler \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)