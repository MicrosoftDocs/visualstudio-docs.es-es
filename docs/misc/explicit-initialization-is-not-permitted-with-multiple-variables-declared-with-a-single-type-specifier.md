---
title: "No se permite la inicializaci&#243;n expl&#237;cita con varias variables declaradas con un solo especificador de tipo | Microsoft Docs"
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
  - "bc30671"
  - "vbc30671"
helpviewer_keywords: 
  - "BC30671"
ms.assetid: 57bbdd58-b58d-4144-8fa6-366a7167df27
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se permite la inicializaci&#243;n expl&#237;cita con varias variables declaradas con un solo especificador de tipo
No se permite la inicialización si se declaran varias variables en la misma línea.  
  
 **Identificador de error:** BC30671  
  
### Para corregir este error  
  
1.  Declare e inicialice cada elemento por separado.  
  
2.  Declare varios elementos juntos y luego inicialice cada uno, por ejemplo:  
  
    ```  
    Dim x, b, i As Integer x = 9 : b = 9 : i = 9 ' ":" is the same as a new line.  
    ```  
  
## Vea también  
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Declaración de variable](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)