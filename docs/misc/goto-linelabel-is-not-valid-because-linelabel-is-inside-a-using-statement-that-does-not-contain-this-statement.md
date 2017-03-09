---
title: "La instrucci&#243;n &#39;GoTo &lt;etiquetaDeL&#237;nea&gt;&#39; no es v&#225;lida porque &#39;&lt;etiquetaDeL&#237;nea&gt;&#39; est&#225; dentro de una instrucci&#243;n &#39;Using&#39; que no contiene esta instrucci&#243;n. | Microsoft Docs"
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
  - "bc36009"
  - "vbc36009"
helpviewer_keywords: 
  - "BC36009"
ms.assetid: ebec3cac-d378-4e9b-a792-12e9ece5599e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;GoTo &lt;etiquetaDeL&#237;nea&gt;&#39; no es v&#225;lida porque &#39;&lt;etiquetaDeL&#237;nea&gt;&#39; est&#225; dentro de una instrucci&#243;n &#39;Using&#39; que no contiene esta instrucci&#243;n.
Una instrucción `GoTo` fuera de una construcción `Using` intenta crear una bifurcación en una etiqueta de línea dentro de la construcción.  
  
 No es válido crear una bifurcación desde cualquier parte fuera de una construcción `Using`...`End Using` a cualquier parte dentro de la construcción.  
  
 **Identificador de error:** BC36009  
  
### Para corregir este error  
  
-   Cambie la etiqueta de línea de la instrucción `GoTo` a una etiqueta que no esté dentro de ninguna construcción `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With` o `Using`...`End Using`.  
  
     O bien  
  
-   Quite la instrucción `GoTo` completamente. La única manera de introducir una construcción `Using`...`End Using` es permitir que el control pase a la propia instrucción `Using`.  
  
## Vea también  
 [GoTo \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/goto-statement)   
 [Using \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/using-statement)