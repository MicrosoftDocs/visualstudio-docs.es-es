---
title: "&#39;especificador&#39; no es v&#225;lido en una declaraci&#243;n de variable miembro. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30235"
  - "bc30235"
helpviewer_keywords: 
  - "BC30235"
ms.assetid: 8c5764e4-0096-4ca0-8656-05341a39833a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;especificador&#39; no es v&#225;lido en una declaraci&#243;n de variable miembro.
Una instrucción `Dim` contiene una palabra clave no válida. Una instrucción `Dim` puede incluir solo las palabras clave `Friend`, `Private`, `Protected`, `Public`, `ReadOnly`, `Shadows`, `Shared` o `Static`.  
  
 Este mensaje también puede aparecer si declara una variable `Static` fuera de un procedimiento. Solo puede usar `Static` en el nivel de procedimiento.  
  
 Tenga en cuenta que si incluye una palabra clave válida en una instrucción `Dim`, se puede omitir la palabra clave `Dim`.  
  
 **Identificador de error:** BC30235  
  
### Para corregir este error  
  
1.  Quite la palabra clave no válida de la instrucción `Dim`.  
  
2.  Si se ha declarado una variable `Static` fuera de un procedimiento, mueva la declaración dentro de un procedimiento o quite la palabra clave `Static`.  
  
## Vea también  
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)