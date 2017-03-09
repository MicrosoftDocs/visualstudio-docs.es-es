---
title: "&#39;&lt;method1&gt;&#39; y &#39;&lt;method2&gt;&#39; no se pueden sobrecargar el uno al otro porque solo se diferencian en par&#225;metros opcionales. | Microsoft Docs"
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
  - "vbc30300"
  - "bc30300"
helpviewer_keywords: 
  - "BC30300"
ms.assetid: adb44ceb-57a0-4123-8fd8-7eb83c3f601f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;method1&gt;&#39; y &#39;&lt;method2&gt;&#39; no se pueden sobrecargar el uno al otro porque solo se diferencian en par&#225;metros opcionales.
Ha intentado sobrecargar un método con otro método que es distinto del primero solo en sus parámetros opcionales. Un método con un parámetro opcional equivale a dos métodos sobrecargados, uno con el parámetro opcional y otro sin él. Por lo tanto, no se puede sobrecargar un método con una lista de argumentos que se corresponda con cualquiera de estos.  
  
 **Identificador de error:** BC30300  
  
### Para corregir este error  
  
-   Asegúrese de que los métodos se diferencian en algo más que en los parámetros.  
  
## Vea también  
 [Sobrecarga de procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Consideraciones sobre la sobrecarga de procedimientos](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)