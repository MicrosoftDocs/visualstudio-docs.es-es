---
title: "Las estructuras no pueden declarar un constructor &#39;Sub New&#39; no compartido sin par&#225;metros | Microsoft Docs"
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
  - "vbc30629"
  - "bc30629"
helpviewer_keywords: 
  - "BC30629"
ms.assetid: f4298ef7-85b1-4543-b764-4c3abda84baa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las estructuras no pueden declarar un constructor &#39;Sub New&#39; no compartido sin par&#225;metros
Los constructores `Sub New` declarados en estructuras deben aceptar argumentos o declararse con el modificador `Shared`.  
  
 **Identificador de error:** BC30629  
  
### Para corregir este error  
  
-   Cambie el constructor `Sub New` para que acepte argumentos.  
  
-   Aplique el modificador `Shared` para hacer que el constructor sea compartido.  
  
## Vea también  
 [Structure \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Estructuras](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)