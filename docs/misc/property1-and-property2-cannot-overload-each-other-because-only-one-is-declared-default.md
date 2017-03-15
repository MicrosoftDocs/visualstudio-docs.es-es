---
title: "&lt;property1&gt; y &lt;property2&gt; no se pueden sobrecargar entre s&#237; porque solo una est&#225; declarada como &#39;Default&#39;. | Microsoft Docs"
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
  - "bc30361"
  - "vbc30361"
helpviewer_keywords: 
  - "BC30361"
ms.assetid: bac85b32-1a1f-4c43-817c-76e209cfeb8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;property1&gt; y &lt;property2&gt; no se pueden sobrecargar entre s&#237; porque solo una est&#225; declarada como &#39;Default&#39;.
Si una propiedad especifica `Default`, todas las propiedades sobrecargadas en ese nombre deben especificar también `Default`.  
  
 **Identificador de error:** BC30361  
  
### Para corregir este error  
  
-   Asegúrese de que todas las propiedades sobrecargadas estén declaradas como `Default`.  
  
## Vea también  
 [Consideraciones sobre la sobrecarga de procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)