---
title: "&#39;ReDim&#39; solo puede cambiar la dimensi&#243;n situada m&#225;s a la derecha | Microsoft Docs"
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
  - "vbrArray_TypeMismatch"
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; solo puede cambiar la dimensi&#243;n situada m&#225;s a la derecha
Una instrucción `ReDim` intentó usar la palabra clave `Preserve` para cambiar una dimensión de una matriz que no es la última dimensión. Si usa `Preserve`, solo puede cambiar el tamaño de la última dimensión de la matriz. Para todas las demás dimensiones, debe especificar el mismo tamaño que la matriz existente.  
  
### Para corregir este error  
  
-   Quite la palabra clave `Preserve`.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Información general sobre matrices en Visual Basic](http://msdn.microsoft.com/es-es/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NO ESTÁ EN LA COMPILACIÓN: Matrices multidimensionales en Visual Basic](http://msdn.microsoft.com/es-es/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [ReDim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Preserve \- delete](http://msdn.microsoft.com/es-es/91badeab-b4e0-48b6-92c9-9f0c8f995d81)