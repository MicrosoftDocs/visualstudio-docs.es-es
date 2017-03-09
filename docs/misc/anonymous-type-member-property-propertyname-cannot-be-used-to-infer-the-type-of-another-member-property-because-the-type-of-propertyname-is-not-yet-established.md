---
title: "La propiedad &#39;&lt;nombreDePropiedad&gt;&#39; del miembro de tipo an&#243;nimo no se puede usar para inferir el tipo de otra propiedad de miembro porque el tipo de &#39;&lt;nombreDePropiedad&gt;&#39; no se ha establecido a&#250;n. | Microsoft Docs"
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
  - "vbc36559"
  - "bc36559"
helpviewer_keywords: 
  - "BC36559"
ms.assetid: 58ab8d35-9d85-4aca-8b4e-f232d7e4af61
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propiedad &#39;&lt;nombreDePropiedad&gt;&#39; del miembro de tipo an&#243;nimo no se puede usar para inferir el tipo de otra propiedad de miembro porque el tipo de &#39;&lt;nombreDePropiedad&gt;&#39; no se ha establecido a&#250;n.
Hasta que se establezca el tipo de una la propiedad de tipo anónimo, no se lo puede usar para establecer el tipo de otra propiedad. Por ejemplo, en la siguiente declaración `.IDName = .LastName` no es válido porque `.LastName` todavía no se ha inicializado.  
  
```  
' Not valid.   
' Dim anon1 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}   
```  
  
 **Identificador de error:** BC36559  
  
### Para corregir este error  
  
-   Establezca el tipo de la propiedad antes de usarlo para inicializar otra propiedad.  
  
    ```  
    Dim anon2 = New With {Key .LastName = "Jones", Key .IDName = .LastName}  
    ```  
  
## Vea también  
 [Tipos anónimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Cómo: Deducir tipos y nombres de propiedades en declaraciones de tipos anónimos](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)