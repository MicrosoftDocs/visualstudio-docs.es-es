---
title: "No se admiten los caracteres de tipo en los alias de importaci&#243;n | Microsoft Docs"
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
  - "vbc31398"
  - "BC31398"
helpviewer_keywords: 
  - "BC31398"
ms.assetid: 0620669d-b529-49f3-9deb-aeda4dacc58a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se admiten los caracteres de tipo en los alias de importaci&#243;n
Una alias de importación de una instrucción `Imports` contiene al menos un carácter de tipo de identificador.  
  
 Un alias de importación debe ser un nombre de Visual Basic válido. Los caracteres permitidos no incluyen ninguno de los caracteres de tipo de identificador \(`%`, `&`, `@`, `!`, `#` y `$`\). Vea [Nombres de elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
 **Identificador de error:** BC31398  
  
### Para corregir este error  
  
-   Quite el carácter o los caracteres de tipo identificador del alias de importación.  
  
## Vea también  
 [Caracteres de tipo](/dotnet/visual-basic/programming-guide/language-features/data-types/type-characters)   
 [Nombres de elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Instrucción Imports \(Tipo y espacio de nombres de .NET\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)   
 [NOTINBUILD: Resolver una referencia cuando varias variables tienen el mismo nombre](http://msdn.microsoft.com/es-es/9601e39f-1911-44e1-ace5-3f6e090408b9)