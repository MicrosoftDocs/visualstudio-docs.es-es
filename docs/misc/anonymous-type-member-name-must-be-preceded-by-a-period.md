---
title: "El nombre de un miembro de tipo an&#243;nimo debe ir precedido de un punto | Microsoft Docs"
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
  - "vbc36575"
  - "bc36575"
helpviewer_keywords: 
  - "BC36575"
ms.assetid: b87be29e-39f0-4830-9969-608d71137e3e
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El nombre de un miembro de tipo an&#243;nimo debe ir precedido de un punto
En la lista de inicializadores de objeto de una declaración de tipo anónimo, un nuevo nombre de miembro al que está asignado un valor debe ir precedido de un punto. En el ejemplo siguiente se muestran una declaración válida y una no válida:  
  
```vb#  
' Valid.  
Dim instanceName1 = New With {.memberName = 10}  
' Invalid declaration that causes this error.  
' Dim instanceName2 = New With {memberName = 10}  
```  
  
 **Identificador de error:** BC36575  
  
### Para corregir este error  
  
-   Agregue un punto antes del nombre de miembro.  
  
## Vea también  
 [Tipos anónimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)