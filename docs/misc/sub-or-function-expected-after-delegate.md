---
title: "Se esperaba &#39;Sub&#39; o &#39;Function&#39; despu&#233;s de &#39;Delegate&#39;. | Microsoft Docs"
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
  - "vbc30278"
  - "bc30278"
helpviewer_keywords: 
  - "BC30278"
ms.assetid: fee206b9-8dc0-436f-9909-abd8c17957f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;Sub&#39; o &#39;Function&#39; despu&#233;s de &#39;Delegate&#39;.
Una instrucción `Delegate` no especifica un procedimiento `Sub` o `Function`. La palabra clave `Sub` o `Function` debe seguir inmediatamente a la palabra clave `Delegate`.  
  
 **Identificador de error:** BC30278  
  
### Para corregir este error  
  
1.  Agregue la palabra clave `Sub` o `Function` inmediatamente después de `Delegate`.  
  
2.  Especifique un nombre de procedimiento, la lista de argumentos y el tipo de valor devuelto según corresponda.  
  
## Vea también  
 [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/index)