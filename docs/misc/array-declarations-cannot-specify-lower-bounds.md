---
title: "Las declaraciones de la matriz no pueden especificar l&#237;mites inferiores | Microsoft Docs"
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
  - "vbc30805"
  - "bc30805"
helpviewer_keywords: 
  - "BC30805"
ms.assetid: f2055387-f4dc-4366-89fb-d752929a0258
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las declaraciones de la matriz no pueden especificar l&#237;mites inferiores
Las matrices siempre tienen un límite inferior de cero. Puede especificar cero como límite inferior para que el código sea más legible. Sin embargo, no puede especificar ningún otro valor para el límite inferior.  
  
 **Identificador de error:** BC30805  
  
### Para corregir este error  
  
-   Defina una dimensión de matrices una unidad por debajo del número total de elementos. Por ejemplo, `Dim y(6)` tiene el mismo tamaño \(7 elementos\) que `Dim x(3 To 9)`. También puede especificar `Dim y(0 To 6)`.  
  
-   Use desplazamientos para simular límites inferiores distintos de cero. En el ejemplo siguiente se simula una matriz con dimensión de 3 a 9.  
  
    ```  
    Const offset As Integer = 3 Dim arrayIndex As Integer ' arrayIndex can vary between 3 and 9. Dim y(0 To 6) ' The preceding statement allocates the same number of elements ' as Dim y(3 To 9). y(arrayIndex - offset) = value ' The preceding statement converts arrayIndex to the ' corresponding index of y.  
    ```  
  
## Vea también  
 [Matrices](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [Dimensiones de matrices en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/array-dimensions)   
 [NO ESTÁ EN LA COMPILACIÓN Cómo: Especificar el límite inferior cero de una matriz](http://msdn.microsoft.com/es-es/20ffd49a-64f7-4634-8ed0-46ba1049d935)