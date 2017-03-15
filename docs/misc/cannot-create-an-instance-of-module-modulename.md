---
title: "No se puede crear una instancia del m&#243;dulo &#39;&lt;nombreM&#243;dulo&gt;&#39;. | Microsoft Docs"
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
  - "bc30166"
  - "vbc30166"
helpviewer_keywords: 
  - "BC30166"
ms.assetid: 40b9dbd3-9b57-450f-a631-b0ab06ca19c4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede crear una instancia del m&#243;dulo &#39;&lt;nombreM&#243;dulo&gt;&#39;.
Un módulo solo existe como una única instancia compartida, y no se pueden crear instancias adicionales.  
  
 **Identificador de error:** BC30166  
  
### Para corregir este error  
  
-   Cambie el módulo por una clase, o reemplácelo en la cláusula `New` con un nombre de clase.  
  
## Vea también  
 [Module \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/module-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Palabra clave Implements e instrucción Implements](http://msdn.microsoft.com/es-es/b96560f7-6413-480f-a1e2-f80253bab5be)