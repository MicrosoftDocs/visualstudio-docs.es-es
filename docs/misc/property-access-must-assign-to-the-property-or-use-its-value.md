---
title: "Debe asignarse un acceso de propiedad a la propiedad o usar su valor. | Microsoft Docs"
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
  - "bc30545"
  - "vbc30545"
helpviewer_keywords: 
  - "BC30545"
ms.assetid: df271c05-1e7a-44e8-bf53-79f06ef916ab
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Debe asignarse un acceso de propiedad a la propiedad o usar su valor.
Ha intentado tener acceso a una propiedad sin asignarlo o usando su valor. El siguiente fragmento de código muestra un ejemplo:  
  
 [!CODE [VbVbalrErrorSamples#1](VbVbalrErrorSamples#1)]  
  
 **Identificador de error:** BC30545  
  
### Para corregir este error  
  
-   Asigne un valor a la propiedad, como se muestra en el siguiente ejemplo:  
  
     [!CODE [VbVbalrErrorSamples#3](VbVbalrErrorSamples#3)]  
  
     O bien  
  
-   Use el valor a la propiedad, como se muestra en el siguiente ejemplo:  
  
     [!CODE [VbVbalrErrorSamples#2](VbVbalrErrorSamples#2)]  
  
## Vea también  
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Operadores de asignación](/dotnet/visual-basic/language-reference/operators/assignment-operators)