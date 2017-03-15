---
title: "Se esperaba &#39;Group&#39; o un identificador | Microsoft Docs"
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
  - "vbc36707"
  - "bc36707"
helpviewer_keywords: 
  - "BC36707"
ms.assetid: 214e4aa3-d20f-41b3-902c-f1076d31b832
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;Group&#39; o un identificador
La parte `Into` de una cláusula `Group By` o `Group Join` no incluye la palabra clave `Group`. Debe incluir la palabra clave `Group` en la cláusula `Into` de una cláusula `Group By` o `Group Join` para identificar el nombre de variable que se usará para los resultados agrupados. Puede ser un nombre que especifique o la palabra clave `Group`.  
  
 **Identificador de error:** BC36707  
  
### Para corregir este error  
  
1.  Asegúrese de que la parte `Into` de la cláusula `Group By` o `Group Join` incluye la palabra clave `Group`, como se muestra en el ejemplo siguiente.  
  
    ```vb#  
    Dim orders = From order In orderList _ Order By order.OrderDate _ Group By OrderDate = order.OrderDate _ Into OrdersByDate = Group  
    ```  
  
## Vea también  
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Group By \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Group Join \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/group-join-clause)