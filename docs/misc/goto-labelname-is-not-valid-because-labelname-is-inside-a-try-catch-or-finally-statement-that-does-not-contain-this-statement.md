---
title: "&#39;GoTo &lt;nombreDeEtiqueta&gt;&#39; no es v&#225;lida porque &#39;&lt;nombreDeEtiqueta&#39; est&#225; dentro de una instrucci&#243;n &#39;Try&#39;, &#39;Catch&#39; o &#39;Finally&#39; que no contiene esta instrucci&#243;n | Microsoft Docs"
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
  - "bc30754"
  - "vbc30754"
helpviewer_keywords: 
  - "BC30754"
ms.assetid: 2eefc7fb-fdf0-41e9-bf60-c3bc93580e14
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;nombreDeEtiqueta&gt;&#39; no es v&#225;lida porque &#39;&lt;nombreDeEtiqueta&#39; est&#225; dentro de una instrucci&#243;n &#39;Try&#39;, &#39;Catch&#39; o &#39;Finally&#39; que no contiene esta instrucci&#243;n
No se puede crear una rama en un bloque `Try...Catch...Finally`.  
  
 **Identificador de error:** BC30754  
  
### Para corregir este error  
  
-   Reestructure el código para que la etiqueta preceda al bloque `Try...Catch...Finally`.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)