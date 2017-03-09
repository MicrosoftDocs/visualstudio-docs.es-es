---
title: "El tipo an&#243;nimo debe contener al menos un miembro. | Microsoft Docs"
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
  - "bc36574"
  - "vbc36574"
helpviewer_keywords: 
  - "BC36574"
ms.assetid: fdc8dd47-ea38-49e8-8dd5-676f726cd101
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo an&#243;nimo debe contener al menos un miembro.
La lista de inicializadores en una declaración de tipo anónimo no puede estar vacía.  
  
```  
' Not valid. ' Dim anonInstance = New With {}  
```  
  
 **Identificador de error:** BC36574  
  
### Para corregir este error  
  
-   Declare un miembro dentro de las llaves, tal como se muestra en el código siguiente.  
  
    ```  
    Dim anonInstance = New With {.MemberName = "value"}  
    ```  
  
## Vea también  
 [Tipos anónimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)