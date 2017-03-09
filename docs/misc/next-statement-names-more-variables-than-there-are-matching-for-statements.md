---
title: "Hay m&#225;s variables designadas por la instrucci&#243;n &#39;Next&#39; de las que corresponden a las instrucciones &#39;For&#39; | Microsoft Docs"
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
  - "bc32037"
  - "vbc32037"
helpviewer_keywords: 
  - "BC32037"
ms.assetid: 7c97d835-1043-40ec-a645-63a053f5f916
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Hay m&#225;s variables designadas por la instrucci&#243;n &#39;Next&#39; de las que corresponden a las instrucciones &#39;For&#39;
Los bucles anidados terminan con una sola instrucción `Next` que especifica más variables de bucle que el número de bucles del anidamiento, como en el ejemplo siguiente:  
  
```  
For I = 1 To 10 For J = 1 To 5 ' ... Next J, I, K   ' Next J, I is valid, but there is no loop on K.  
```  
  
 **Id. de error:** BC32037  
  
### Para corregir este error  
  
1.  Asegúrese de que la instrucción `Next` especifica todas las variables de bucle anidado en el orden inverso del inicio del bucle.  
  
2.  Quite las variables superfluas de la instrucción `Next`.  
  
## Vea también  
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)