---
title: "Se esperaba &#39;And&#39;. | Microsoft Docs"
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
  - "vbc36620"
  - "bc36620"
helpviewer_keywords: 
  - "BC36620"
ms.assetid: b3d21d4d-86c0-44d2-8afc-c19d375e9ddd
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;And&#39;.
Un operador de comparación distinto de `And` se ha usado para combinar dos o más operadores `Equals` en una cláusula `Join` o `Group Join`. Solo el operador `And` tiene permitido combinar varios operadores `Equals` en una cláusula `Join` o `Group Join`.  
  
 **Identificador de error:** BC36620  
  
### Para corregir este error  
  
1.  Reestructure las cláusulas `Equals` para realizar comparaciones usando solo el operador `And`. A continuación se muestra un ejemplo:  
  
    ```vb#  
    Dim petOwnersJoin = From pers In people _  
                        Join pet In pets _  
                        On pet.Owner Equals pers And _  
                           pet.Name = pers.PetName_  
                        Select pers, pet  
    ```  
  
## Vea también  
 [Cómo: Combinar datos con cláusulas Join](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Join \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)