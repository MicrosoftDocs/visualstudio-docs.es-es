---
title: "La propiedad &#39;WriteOnly&#39; debe proporcionar una instrucci&#243;n &#39;Set&#39; | Microsoft Docs"
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
  - "bc30125"
  - "vbc30125"
helpviewer_keywords: 
  - "BC30125"
ms.assetid: c2b18086-9cd9-4094-b9a9-491c8d617096
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propiedad &#39;WriteOnly&#39; debe proporcionar una instrucci&#243;n &#39;Set&#39;
Si una propiedad se declara como `WriteOnly`, debe proporcionar un procedimiento para escribir su valor.  
  
 **Identificador de error:** BC30125  
  
### Para corregir este error  
  
1.  Asegúrese de incluir un procedimiento `Set` entre la instrucción `Property` y la instrucción `End Property`.  
  
2.  Compruebe que otros procedimientos de la declaración `Property` finalicen correctamente.  
  
## Vea también  
 [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Set \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/set-statement)