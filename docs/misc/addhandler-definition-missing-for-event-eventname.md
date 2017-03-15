---
title: "Falta la definici&#243;n de &#39;AddHandler&#39; del evento &#39;&lt;eventname&gt;&#39; | Microsoft Docs"
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
  - "bc31130"
  - "vbc31130"
helpviewer_keywords: 
  - "BC31130"
ms.assetid: cf6c7fd6-ce2e-4916-b427-2a4a63e7279d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Falta la definici&#243;n de &#39;AddHandler&#39; del evento &#39;&lt;eventname&gt;&#39;
Si un evento se declara como `Custom`, debe facilitar un procedimiento para agregar un controlador de eventos.  
  
 **Id. de error:** BC31130  
  
### Para corregir este error  
  
1.  Incluya una declaración `AddHandler` entre la instrucción `Custom Event` y la instrucción `End Event`.  
  
2.  Compruebe que otros procedimientos dentro de la declaración del evento terminen correctamente.  
  
## Vea también  
 [AddHandler \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)