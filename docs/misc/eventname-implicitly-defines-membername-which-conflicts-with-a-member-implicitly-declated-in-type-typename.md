---
title: "El evento &#39;&lt;nombreDeEvento&gt;&#39; define impl&#237;citamente a &#39;&lt;nombreDeMiembro&gt;&#39;, que entra en conflicto con un miembro impl&#237;citamente declarado en &lt;tipo&gt; &#39;&lt;nombreDeTipo&gt;&#39; | Microsoft Docs"
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
  - "bc31059"
  - "vbc31059"
helpviewer_keywords: 
  - "BC31059"
ms.assetid: 60ddb2f4-a204-41eb-b13b-b2bb13ddb69c
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El evento &#39;&lt;nombreDeEvento&gt;&#39; define impl&#237;citamente a &#39;&lt;nombreDeMiembro&gt;&#39;, que entra en conflicto con un miembro impl&#237;citamente declarado en &lt;tipo&gt; &#39;&lt;nombreDeTipo&gt;&#39;
El nombre de un miembro de tipo está en conflicto con el nombre de un miembro creado implícitamente para un evento. Los eventos crean implícitamente varias variables. Por ejemplo, la declaración `Event X` declara implícitamente los nombres `XEventHandler`, `XEvent`, `add_X` y `remove_X`.  
  
 **Identificador de error:** BC31059  
  
### Para corregir este error  
  
-   Cambie el nombre del miembro declarado explícitamente para resolver el conflicto de nomenclatura.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Instrucciones de declaración en Visual Basic](http://msdn.microsoft.com/es-es/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)