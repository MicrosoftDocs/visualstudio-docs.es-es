---
title: "Se esperaba &#39;By&#39; | Microsoft Docs"
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
  - "vbc36605"
  - "bc36605"
helpviewer_keywords: 
  - "BC36605"
ms.assetid: d0397b6e-bfc2-400c-92fc-efe82036cfdb
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;By&#39;
Se ha especificado una cláusula `Order By` o `Group By` sin la palabra clave `By`.  
  
 **Id. de error:** BC36605  
  
### Para corregir este error  
  
1.  Agregue la palabra clave `By` a las cláusulas `Order By` o `Group By`. A continuación se muestra un ejemplo:  
  
    ```vb#  
    Dim customersByCountry = From cust In customers _  
                             Order By cust.Country, cust.City _  
                             Group By CountryName = cust.Country _  
                             Into RegionalCustomers = Group, Count() _  
                             Order By CountryName  
    ```  
  
## Vea también  
 [Cómo: Ordenar los resultados de una consulta](../Topic/How%20to:%20Sort%20Query%20Results%20by%20Using%20LINQ%20\(Visual%20Basic\).md)   
 [Order By \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/order-by-clause)   
 [Group By \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)