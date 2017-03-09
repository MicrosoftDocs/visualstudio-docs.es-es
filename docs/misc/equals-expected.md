---
title: "Se esperaba &#39;Equals&#39; | Microsoft Docs"
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
  - "vbc36619"
  - "bc36619"
helpviewer_keywords: 
  - "BC36619"
ms.assetid: 1fd8c0dc-0e87-47b7-ab30-498809cca033
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;Equals&#39;
Se especificó una cláusula `Join` o `Group Join` sin un operador `Equals`. Usa el operador `Equals` para identificar la operación `Boolean` con el fin de probar los campos clave de elementos coincidentes.  
  
 **Identificador de error:** BC36619  
  
### Para corregir este error  
  
1.  Agregue el operador `Equals` y los campos clave a la cláusula `Join` o `Group Join`. Por ejemplo:  
  
    ```vb#  
    Dim petOwnersGrouped = From pers In people _ Group Join pet In pets _ On pers Equals pet.Owner _ Into PetList = Group _ Select pers.FirstName, pers.LastName, _ PetList  
    ```  
  
## Vea también  
 [Cómo: Combinar datos con cláusulas Join](../Topic/How%20to:%20Combine%20Data%20with%20LINQ%20by%20Using%20Joins%20\(Visual%20Basic\).md)   
 [Join \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)