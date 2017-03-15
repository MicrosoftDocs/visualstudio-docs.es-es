---
title: "La instrucci&#243;n &#39;Loop&#39; no puede tener una condici&#243;n si la instrucci&#243;n &#39;Do&#39; coincidente tiene una. | Microsoft Docs"
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
  - "vbc30238"
  - "bc30238"
helpviewer_keywords: 
  - "BC30238"
ms.assetid: 81513cb5-69e7-4d62-b33e-e54cb8c5e8bf
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;Loop&#39; no puede tener una condici&#243;n si la instrucci&#243;n &#39;Do&#39; coincidente tiene una.
Una instrucción `Loop` contiene una cláusula `While` o `Until` y la instrucción `Do` correspondiente también contiene una cláusula de ese tipo. Solo una de las instrucciones `Do` y `Loop` de un bucle puede especificar una condición.  
  
 **Identificador de error:** BC30238  
  
### Para corregir este error  
  
-   Quite la cláusula `While` o `Until` de la instrucción `Do` o la instrucción `Loop`.  
  
## Vea también  
 [Do...Loop \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/do-loop-statement)