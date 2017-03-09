---
title: "Se esperaba &#39;Join&#39; | Microsoft Docs"
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
  - "vbc36631"
  - "bc36631"
helpviewer_keywords: 
  - "BC36631"
ms.assetid: bb2b03b6-6784-423a-b91a-cb7066c1d093
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;Join&#39;
Se especificó una cláusula `Group Join` sin una palabra clave `Join`.  
  
 **Identificador de error:** BC36631  
  
### Para corregir este error  
  
1.  Agregue la palabra clave `Join` a la cláusula `Group Join`, tal como se muestra en el ejemplo siguiente:  
  
    ```vb#  
    Dim query = From var1 In collection1 _ Join var2 In collection2 _ Group Join var3 In collection3 _ On var2.ID Equals var3 Into Matches = Group _ On var1 Equals var2.ID _ Select JoinID = var1, var2.Name, Matches  
    ```  
  
## Vea también  
 [Cómo: Combinar datos con cláusulas Join](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Group Join \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)