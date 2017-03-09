---
title: "Las instrucciones &#39;ReDim&#39; necesitan una lista entre par&#233;ntesis de los nuevos l&#237;mites de cada una de las dimensiones de la matriz. | Microsoft Docs"
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
  - "bc30670"
  - "vbc30670"
helpviewer_keywords: 
  - "BC30670"
ms.assetid: b2c5fea3-e7db-4797-b917-d61a65befbd4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las instrucciones &#39;ReDim&#39; necesitan una lista entre par&#233;ntesis de los nuevos l&#237;mites de cada una de las dimensiones de la matriz.
Debe especificar el nuevo tamaño de una matriz como parte de una instrucción `ReDim`.  
  
 **Identificador de error:** BC30670  
  
### Para corregir este error  
  
-   Proporcione el tamaño de cada rango de la matriz; por ejemplo:  
  
    ```  
    ReDim arr(5, 6)  
    ```  
  
## Vea también  
 [ReDim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/redim-statement)