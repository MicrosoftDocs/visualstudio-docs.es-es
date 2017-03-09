---
title: "Se esperaba &#39;In&#39; | Microsoft Docs"
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
  - "bc36607"
  - "vbc36607"
helpviewer_keywords: 
  - "BC36607"
ms.assetid: f390bca5-12fe-4fe1-bd86-7f8ab66dfbd8
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;In&#39;
Se especificó una cláusula `From` o `Aggregate` sin un operador `In`. El operador `In` se usa para identificar la colección que se va a consultar.  
  
 **Identificador de error:** BC36607  
  
### Para corregir este error  
  
1.  Agregue el operador `In` y los campos clave a la cláusula `From` o `Aggregate`. A continuación se muestra un ejemplo:  
  
    ```vb#  
    Dim names = From pers In people Select pers.FirstName, pers.LastName  
    ```  
  
## Vea también  
 [From \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/from-clause)   
 [Aggregate \(Cláusula\)](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)