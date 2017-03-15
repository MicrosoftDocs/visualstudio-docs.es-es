---
title: "Los descriptores de acceso de la propiedad no se pueden declarar como &#39;&lt;keyword&gt;&#39;. | Microsoft Docs"
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
  - "vbc31099"
  - "bc31099"
helpviewer_keywords: 
  - "BC31099"
ms.assetid: d6f3b989-39b9-4c47-995a-bd83ec03d7b8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los descriptores de acceso de la propiedad no se pueden declarar como &#39;&lt;keyword&gt;&#39;.
Una declaración de procedimiento `Get` o `Set` incluye una palabra clave que no es válida en un procedimiento de propiedad.  
  
 [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement) y [Set \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/set-statement) solo permiten un modificador de acceso \(`Public`, `Protected`, `Friend`, `Protected Friend`, `Private`\).  
  
 **Identificador de error:** BC31099  
  
### Para corregir este error  
  
-   Quite la palabra clave no válida de la instrucción `Get` o `Set`.  
  
## Vea también  
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Cómo: Declarar una propiedad con niveles de acceso mixtos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)