---
title: "No se puede acceder a &#39;&lt;m&#233;todo&gt;&#39; en este contexto porque es &#39;&lt;modificador&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30389"
  - "bc30389"
helpviewer_keywords: 
  - "BC30389"
ms.assetid: fae58a68-df91-4741-a8c9-f1bb10e166e2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede acceder a &#39;&lt;m&#233;todo&gt;&#39; en este contexto porque es &#39;&lt;modificador&gt;&#39;
Intentó acceder a un método que no es accesible en este contexto porque se declaró `Private`. Una posible causa de este error es que el compilador de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] importa todos los miembros de una clase y distingue mayúsculas de minúsculas, por lo que los nombres que solo se diferencias en las mayúsculas y minúsculas podrían entrar en conflicto.  
  
 **Identificador de error:** BC30389  
  
### Para corregir este error  
  
-   Considere la posibilidad de declarar el método `Public`.  
  
-   Si el error está causado por un conflicto de nombres, diferencie los nombres en conflicto de otro modo aparte de las mayúsculas y minúsculas.  
  
## Vea también  
 [Private](/dotnet/visual-basic/language-reference/modifiers/private)