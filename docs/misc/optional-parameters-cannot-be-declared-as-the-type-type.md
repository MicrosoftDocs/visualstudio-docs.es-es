---
title: "Los par&#225;metros opcionales no se pueden declarar como el tipo &#39;&lt;tipo&gt;&#39; | Microsoft Docs"
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
  - "bc30423"
  - "vbc30423"
helpviewer_keywords: 
  - "BC30423"
ms.assetid: 972dab8b-d91e-4a89-b822-2b8e4aadd25f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los par&#225;metros opcionales no se pueden declarar como el tipo &#39;&lt;tipo&gt;&#39;
Los parámetros opcionales no pueden ser del tipo de datos de una estructura.  
  
 **Identificador de error:** BC30423  
  
### Para corregir este error  
  
1.  Para pasar una estructura a un parámetro opcional, declare el parámetro como `Object`.  
  
2.  Use `CType` para convertir el parámetro a ese tipo de estructura dentro del procedimiento.  
  
## Vea también  
 [Estructuras y clases](/dotnet/visual-basic/programming-guide/language-features/data-types/structures-and-classes)   
 [CType \(Función\)](/dotnet/visual-basic/language-reference/functions/ctype-function)