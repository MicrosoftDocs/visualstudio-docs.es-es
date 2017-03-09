---
title: "&#39;GoTo &lt;nombreDeEtiqueta&gt;&#39; no es v&#225;lida porque &#39;&lt;nombreDeEtiqueta&#39; est&#225; dentro de una instrucci&#243;n &#39;With&#39; que no contiene esta instrucci&#243;n | Microsoft Docs"
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
  - "bc30756"
  - "vbc30756"
helpviewer_keywords: 
  - "BC30756"
ms.assetid: 9c39d4ad-0b9b-45e9-b6c2-d983144b5b23
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;nombreDeEtiqueta&gt;&#39; no es v&#225;lida porque &#39;&lt;nombreDeEtiqueta&#39; est&#225; dentro de una instrucci&#243;n &#39;With&#39; que no contiene esta instrucci&#243;n
Las instrucciones `GoTo` se restringen a los saltos dentro del bloque actual del código.  
  
 **Identificador de error:** BC30756  
  
### Para corregir este error  
  
-   Reestructure el código para que tanto la instrucción `GoTo` como la etiqueta estén dentro del bloque `With`.  
  
## Vea también  
 [GoTo \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/goto-statement)