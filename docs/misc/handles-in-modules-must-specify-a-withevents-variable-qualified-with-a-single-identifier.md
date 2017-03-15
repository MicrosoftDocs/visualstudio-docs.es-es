---
title: "&#39;Handles&#39; en los m&#243;dulos debe especificar una variable &#39;WithEvents&#39; calificada con un identificador &#250;nico | Microsoft Docs"
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
  - "bc31418"
  - "vbc31418"
helpviewer_keywords: 
  - "BC31418"
ms.assetid: 7d866577-1e42-43f1-85d1-5d7eeba881b2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Handles&#39; en los m&#243;dulos debe especificar una variable &#39;WithEvents&#39; calificada con un identificador &#250;nico
Para especificar un controlador de eventos, las instrucciones  `Handles` deben especificar una variable de objeto declarada con la palabra clave `WithEvents`.  
  
 **Id. de error:** BC31418  
  
### Para corregir este error  
  
-   Use el modificador `WithEvents` para declarar las variables que se usarán con la instrucción `Handles`.  
  
## Vea también  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)