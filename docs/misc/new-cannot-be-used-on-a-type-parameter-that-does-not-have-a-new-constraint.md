---
title: "&#39;New&#39; no se puede usar en un par&#225;metro de tipo que no tenga una restricci&#243;n &#39;New&#39; | Microsoft Docs"
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
  - "bc32046"
  - "vbc32046"
helpviewer_keywords: 
  - "BC32046"
ms.assetid: 7ec6b52d-6fd5-47a0-b4a2-163bfd3dae35
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; no se puede usar en un par&#225;metro de tipo que no tenga una restricci&#243;n &#39;New&#39;
Una instrucción de declaración usa una cláusula [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator) que especifica un parámetro de tipo como el tipo que se va a crear y el parámetro de tipo se declara sin una restricción `New`.  
  
 Una *restricción* en un parámetro de tipo impone un requisito en cualquier argumento de tipo pasado a ese parámetro de tipo al crear el tipo genérico. La restricción `New` especifica que el argumento de tipo debe exponer un constructor sin parámetros al que el código de creación pueda acceder. Esto es lo que permite que una cláusula `New` en una instrucción de declaración pueda crear una instancia de ese tipo.  
  
 **Identificador de error:** BC32046  
  
### Para corregir este error  
  
-   Si puede exigir que el argumento de tipo exponga un constructor sin parámetros accesible, agregue la restricción `New` a la declaración del parámetro de tipo.  
  
-   Si no puede exigir que el argumento de tipo exponga un constructor sin parámetros accesible, quite la cláusula `New` de la instrucción de declaración. No puede garantizar que cualquier argumento de tipo pasado a ese parámetro de tipo permita la creación de una instancia.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)