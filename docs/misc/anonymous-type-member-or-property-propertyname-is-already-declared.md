---
title: "El miembro de tipo an&#243;nimo o la propiedad &#39;&lt;nombreDePropiedad&gt;&#39; ya est&#225;n declarados | Microsoft Docs"
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
  - "bc36547"
  - "vbc36547"
helpviewer_keywords: 
  - "BC36547"
ms.assetid: 4c60d24a-62d7-404a-bc35-d1a1d9c9f851
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El miembro de tipo an&#243;nimo o la propiedad &#39;&lt;nombreDePropiedad&gt;&#39; ya est&#225;n declarados
Un nombre de propiedad puede establecerse solo una vez en la declaración de un tipo anónimo. Por ejemplo, las siguientes declaraciones no son válidas:  
  
```vb#  
'' Not valid, because the Label property is assigned to twice.  
' Dim anonType1 = New With {.Label = "Debra Garcia", .Label = .Label & ", President"}  
'' Not valid, because the property name inferred for both properties is  
'' Name.  
' Dim anonType2 = New With {Key product.Name, Key car1.Name}  
```  
  
 **Identificador de error:** BC36547  
  
### Para corregir este error  
  
-   Elija otro nombre para una de las propiedades.  
  
    ```vb#  
    ' Valid.  
    Dim anonType3 = New With {.Name = "Debra Garcia", .Label = .Name & ", President"}  
    ```  
  
-   Proporcione nombres nuevos para las variables o los nombres de propiedad de las que se están infiriendo nombres y valores.  
  
    ```vb#  
    ' Valid.  
    Dim anonType4 = New With {Key .ProductName = product.Name, Key .CarName = car1.Name}  
  
    ```  
  
## Vea también  
 [Tipos anónimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Cómo: Deducir tipos y nombres de propiedades en declaraciones de tipos anónimos](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)