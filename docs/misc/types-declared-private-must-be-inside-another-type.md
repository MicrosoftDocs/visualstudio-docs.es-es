---
title: "Los tipos declarados como &#39;Private&#39; deben estar dentro de otro tipo. | Microsoft Docs"
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
  - "vbc31089"
  - "bc31089"
helpviewer_keywords: 
  - "BC31089"
ms.assetid: 44ea5fe4-4af6-4cea-a4a5-2cf966df2937
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos declarados como &#39;Private&#39; deben estar dentro de otro tipo.
El modificador `Private` se usó en un tipo que no está dentro de otro tipo.  
  
 **Identificador de error:** BC31089  
  
### Para corregir este error  
  
1.  Use un modificador de acceso menos restrictivo, como `Friend`.  
  
2.  Declare el tipo dentro de otro tipo.  
  
## Vea también  
 [Private](/dotnet/visual-basic/language-reference/modifiers/private)