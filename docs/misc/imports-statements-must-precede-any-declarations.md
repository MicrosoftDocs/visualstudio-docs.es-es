---
title: "Las instrucciones &#39;Imports&#39; deben preceder a cualquier declaraci&#243;n. | Microsoft Docs"
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
  - "vbc30465"
  - "bc30465"
helpviewer_keywords: 
  - "BC30465"
ms.assetid: 726365f6-d6fc-454a-a43b-afa41bfea82a
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las instrucciones &#39;Imports&#39; deben preceder a cualquier declaraci&#243;n.
Una instrucción `Imports` sigue a una instrucción de declaración dentro de un archivo de origen.  
  
 La instrucción `Imports` importa nombres de espacios de nombres de ensamblados y proyectos a los que se hace referencia, así como nombres de los espacios de nombres definidos dentro del mismo proyecto como en el que aparece. Las instrucciones `Imports` deben colocarse en un archivo de origen antes de las referencias a identificadores.  
  
 **Identificador de error:** BC30465  
  
### Para corregir este error  
  
-   Mueva la instrucción `Imports` a la parte superior del archivo de origen, antes de cualquier instrucción de declaración.  
  
## Vea también  
 [Instrucción Imports \(Tipo y espacio de nombres de .NET\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type)