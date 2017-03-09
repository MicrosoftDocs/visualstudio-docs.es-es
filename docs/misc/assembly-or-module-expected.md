---
title: "Se esperaba &#39;Assembly&#39; o &#39;Module&#39;. | Microsoft Docs"
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
  - "vbc32015"
  - "bc32015"
helpviewer_keywords: 
  - "BC32015"
ms.assetid: 6e62fe8d-a875-4995-b6b2-443e75c65e85
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;Assembly&#39; o &#39;Module&#39;.
Se ha especificado un atributo global sin indicar si se aplica a todo el ensamblado o solo al módulo actual. Los atributos globales deben especificar `Assembly` o `Module`.  
  
 Un atributo global es aquel que aparece en una línea de código fuente por sí mismo, en lugar de aplicarse a la declaración de un elemento de programación determinado.  
  
 **Identificador de error:** BC32015  
  
### Para corregir este error  
  
1.  Si desea que el atributo sea global, agregue la palabra clave `Assembly` o `Module` al principio del bloque de atributos, seguido de dos puntos \(:\).  
  
2.  Si no desea que el atributo sea global, elimine el bloque de atributos o muévalo a una declaración de elemento de programación.  
  
## Vea también  
 [Assembly](/dotnet/visual-basic/language-reference/modifiers/assembly)   
 [Module \<palabra clave\>](../Topic/Module%20%3Ckeyword%3E%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos globales de Visual Basic](http://msdn.microsoft.com/es-es/253a32d8-1531-4504-b687-088554ab71d2)