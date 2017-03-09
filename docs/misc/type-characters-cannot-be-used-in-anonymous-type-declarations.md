---
title: "No se pueden usar caracteres de tipo en declaraciones de tipo an&#243;nimo | Microsoft Docs"
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
  - "bc36560"
  - "vbc36560"
helpviewer_keywords: 
  - "BC36560"
ms.assetid: 70eee559-d6fc-409b-b835-2c84511b160e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden usar caracteres de tipo en declaraciones de tipo an&#243;nimo
No puede usar un carácter de tipo en un nombre de propiedad cuando se declara una instancia de un tipo anónimo. El tipo de datos de la propiedad se deduce del valor asignado a él. Por ejemplo, las siguientes declaraciones no son válidas:  
  
```vb#  
'' Not valid. 'Dim anon1 = New With {.ID$ = "abc"} 'Dim anon2 = New With {.ID$ = 42}  
```  
  
 **Identificador de error:** BC36560  
  
### Para corregir este error  
  
-   Quite el carácter de tipo de la lista de inicializadores. Puede convertir explícitamente el valor asignado si es necesario para establecer el tipo de datos que desee para la propiedad.  
  
    ```vb#  
    ' Valid. Dim anon1 = New With {.ID = "abc"} Dim anon2 = New With {.ID = CStr(42)}  
    ```  
  
## Vea también  
 [Tipos anónimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Cómo: Deducir tipos y nombres de propiedades en declaraciones de tipos anónimos](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)   
 [Conversiones implícitas y explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)