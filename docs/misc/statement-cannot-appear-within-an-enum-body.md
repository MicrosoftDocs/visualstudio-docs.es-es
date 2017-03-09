---
title: "La instrucci&#243;n no puede aparecer dentro del cuerpo de una enumeraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30619"
  - "bc30619"
helpviewer_keywords: 
  - "BC30619"
ms.assetid: 5d91d601-2a2d-418c-ae26-791d14a6f3cd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n no puede aparecer dentro del cuerpo de una enumeraci&#243;n
La instrucción no puede aparecer dentro del cuerpo de una enumeración. Se supone el final de la enumeración.  
  
 Se encontró una construcción de lenguaje inesperada. Se supone que falta una construcción `End Enum` y que cualquier código fuente después de este punto está fuera de la enumeración.  
  
 **Identificador de error:** BC30619  
  
### Para corregir este error  
  
1.  Compruebe la sintaxis del código usado dentro de la enumeración.  
  
2.  Asegúrese de que la definición de la interfaz finaliza con una construcción `End Enum`.  
  
## Vea también  
 [Enum \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/enum-statement)