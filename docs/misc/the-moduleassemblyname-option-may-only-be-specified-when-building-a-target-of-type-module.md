---
title: "La opci&#243;n /moduleassemblyname solo se puede especificar al crear un destino de tipo &#39;module&#39; | Microsoft Docs"
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
  - "bc2030"
  - "vbc2030"
helpviewer_keywords: 
  - "BC2030"
ms.assetid: 2ebc577b-3464-40cc-8788-9fc9d3b4f928
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La opci&#243;n /moduleassemblyname solo se puede especificar al crear un destino de tipo &#39;module&#39;
Se pasó al compilador de Visual Basic la opción del compilador `/moduleassemblyname` cuando la opción `/target` estaba establecida en un valor diferente de `module`.  
  
 **Identificador de error:** BC2030  
  
### Para corregir este error  
  
1.  Quite la opción del compilador `/moduleassemblyname` o establezca la opción `/target` en `module`.  
  
## Vea también  
 [\/target](/dotnet/visual-basic/reference/command-line-compiler/target)   
 [\/moduleassemblyname](/dotnet/visual-basic/reference/command-line-compiler/moduleassemblyname)   
 [Compilador de línea de comandos de Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/index)