---
title: "La sobrecarga de m&#233;todos declarada en varias interfaces base no es v&#225;lida | Microsoft Docs"
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
  - "bc31410"
  - "vbc31410"
helpviewer_keywords: 
  - "BC31410"
ms.assetid: 7d1831c2-837c-4b02-8492-d0fc038fe184
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La sobrecarga de m&#233;todos declarada en varias interfaces base no es v&#225;lida
Varias interfaces heredadas sobrecargan el mismo método de manera implícita.  
  
 **Id. de error:** BC31410  
  
### Para corregir este error  
  
-   Use el modificador `Shadows` en lugar del modificador `Overloads`.  
  
## Vea también  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)