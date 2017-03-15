---
title: "La propiedad &#39;ReadOnly&#39; debe proporcionar una instrucci&#243;n &#39;Get&#39; | Microsoft Docs"
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
  - "bc30126"
  - "vbc30126"
helpviewer_keywords: 
  - "BC30126"
ms.assetid: a522c39e-1f11-45c8-a00b-3546c842909a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propiedad &#39;ReadOnly&#39; debe proporcionar una instrucci&#243;n &#39;Get&#39;
Si una propiedad se declara como `ReadOnly`, debe proporcionar un procedimiento para leer su valor.  
  
 **Identificador de error:** BC30126  
  
### Para corregir este error  
  
1.  Asegúrese de incluir un procedimiento `Get` entre la instrucción `Property` y la instrucción `End Property`.  
  
2.  Compruebe que otros procedimientos de la declaración `Property` finalicen correctamente.  
  
## Vea también  
 [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement)