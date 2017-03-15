---
title: "&lt;type1&gt; &#39;&lt;typename1&gt;&#39; est&#225; en conflicto con un miembro declarado impl&#237;citamente para el evento &#39;&lt;eventname&gt;&#39; en &lt;type2&gt; &#39;&lt;typename2&gt;&#39;. | Microsoft Docs"
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
  - "vbc31061"
  - "bc31061"
helpviewer_keywords: 
  - "BC31061"
ms.assetid: de5b1121-8c8f-4aba-a3e7-1e3e60df0dc5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt; &#39;&lt;typename1&gt;&#39; est&#225; en conflicto con un miembro declarado impl&#237;citamente para el evento &#39;&lt;eventname&gt;&#39; en &lt;type2&gt; &#39;&lt;typename2&gt;&#39;.
El nombre de un miembro de tipo está en conflicto con el nombre de un miembro creado implícitamente para un evento. Los eventos crean implícitamente varias variables implícitas. Por ejemplo, la declaración `Event X` declara implícitamente los nombres `XEventHandler`, `XEvent`, `add_X` y `remove_X`.  
  
 **Identificador de error:** BC31061  
  
### Para corregir este error  
  
-   Cambie el nombre del miembro declarado explícitamente para quitar los conflictos de nombres.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Instrucciones de declaración en Visual Basic](http://msdn.microsoft.com/es-es/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)