---
title: "La variable de control de bucle &#39;For&#39; no puede ser del tipo &#39;&lt;tipo&gt;&#39; | Microsoft Docs"
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
  - "vbc30337"
  - "bc30337"
helpviewer_keywords: 
  - "BC30337"
ms.assetid: 988bba15-e9a2-4045-98a0-7f53c8b2c3e3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable de control de bucle &#39;For&#39; no puede ser del tipo &#39;&lt;tipo&gt;&#39;
Ha intentado usar una variable de control de bucle que no es de un tipo válido. Al principio de un bucle `For`, el punto inicial, el punto final y el valor de incremento se evalúan en orden textual. Las tres expresiones deben poder convertirse implícitamente al tipo de la variable. Si la variable de bucle `For` es de tipo `Object`, al menos una de las expresiones en tiempo de ejecución debe ser de tipo numérico y las tres expresiones deben poder convertirse al tipo numérico más amplio de ellas.  
  
 **Identificador de error:** BC30337  
  
### Para corregir este error  
  
-   Compruebe el tipo de la variable de control de bucle y cámbielo a uno válido.  
  
## Vea también  
 [For \(Visual Basic\)](http://msdn.microsoft.com/es-es/c470a263-9b49-4308-8fd6-8592b84a7980)   
 [Do...Loop \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/do-loop-statement)   
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)