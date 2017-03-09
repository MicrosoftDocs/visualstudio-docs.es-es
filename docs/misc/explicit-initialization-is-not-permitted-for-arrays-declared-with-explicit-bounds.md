---
title: "No se permite la inicializaci&#243;n expl&#237;cita para matrices declaradas con l&#237;mites expl&#237;citos | Microsoft Docs"
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
  - "bc30672"
  - "vbc30672"
helpviewer_keywords: 
  - "BC30672"
ms.assetid: 4b525e8d-bde5-4408-8c10-7605ca039f0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se permite la inicializaci&#243;n expl&#237;cita para matrices declaradas con l&#237;mites expl&#237;citos
Las matrices no se pueden inicializar si están declaradas con un tamaño específico.  
  
 **Identificador de error:** BC30672  
  
### Para corregir este error  
  
-   Declare la matriz y, después, inicialícela por separado.  
  
-   Declárela e inicialícela como una matriz dinámica y use `ReDim` si es necesario; por ejemplo:  
  
    ```  
    Dim A() As Integer = {0, 1, 2, 3} ReDim Preserve A(3)  
    ```  
  
## Vea también  
 [Matrices](/dotnet/visual-basic/programming-guide/language-features/arrays/index)