---
title: "&#39;GoTo &lt;nombreDeEtiqueta&gt;&#39; no es v&#225;lida porque &#39;&lt;nombreDeEtiqueta&gt;&#39; est&#225; dentro de una instrucci&#243;n &#39;For&#39; o &#39;For Each&#39; que no contiene esta instrucci&#243;n | Microsoft Docs"
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
  - "vbc30757"
  - "bc30757"
helpviewer_keywords: 
  - "BC30757"
ms.assetid: be28bec5-1bc4-4da1-ba0c-4e3faac81077
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;GoTo &lt;nombreDeEtiqueta&gt;&#39; no es v&#225;lida porque &#39;&lt;nombreDeEtiqueta&gt;&#39; est&#225; dentro de una instrucci&#243;n &#39;For&#39; o &#39;For Each&#39; que no contiene esta instrucci&#243;n
Las instrucciones `GoTo` se restringen a los saltos dentro del bloque actual del código.  
  
 **Identificador de error:** BC30757  
  
### Para corregir este error  
  
-   Reestructure el código para que tanto la instrucción `GoTo` como la etiqueta estén dentro del bloque `For`.  
  
## Vea también  
 [GoTo \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/goto-statement)   
 [For \(Visual Basic\)](http://msdn.microsoft.com/es-es/c470a263-9b49-4308-8fd6-8592b84a7980)