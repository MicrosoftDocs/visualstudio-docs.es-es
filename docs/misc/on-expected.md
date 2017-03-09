---
title: "Se esperaba &#39;On&#39; | Microsoft Docs"
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
  - "bc36618"
  - "vbc36618"
helpviewer_keywords: 
  - "BC36618"
ms.assetid: 7cb1b205-c4c3-4485-ae3f-8942425692ff
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;On&#39;
Se especificó una cláusula `Join` o `Group Join` sin un operador `On`. El operador `On` se usa para identificar el campo clave de la variable de rango de cada colección. Los campos clave se usan para hacer coincidir los elementos de cada colección.  
  
 **Identificador de error:** BC36618  
  
### Para corregir este error  
  
1.  Agregue el operador `On` y los campos clave a la cláusula `Join` o `Group Join`. A continuación se muestra un ejemplo:  
  
    ```vb#  
    Dim petOwnersJoin = From pers In people _ Join pet In pets _ On pet.Owner Equals pers _ Select pers.FirstName, PetName = pet.Name  
    ```  
  
## Vea también  
 [Cómo: Combinar datos con cláusulas Join](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Join \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)