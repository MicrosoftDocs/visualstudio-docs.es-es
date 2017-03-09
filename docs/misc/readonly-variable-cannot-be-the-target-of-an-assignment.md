---
title: "La variable &#39;ReadOnly&#39; no puede ser el destino de una asignaci&#243;n | Microsoft Docs"
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
  - "vbc30064"
  - "bc30064"
helpviewer_keywords: 
  - "BC30064"
ms.assetid: 17e0751d-4c22-40b2-bb07-cb5c845dbc30
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable &#39;ReadOnly&#39; no puede ser el destino de una asignaci&#243;n
Se encontró una propiedad `ReadOnly` en un contexto que le asigna un valor. Solo se pueden asignar valores durante la ejecución a variables, propiedades y elementos de matriz en los que se pueda escribir.  
  
 **Identificador de error:** BC30064  
  
### Para corregir este error  
  
-   Quite la palabra clave `ReadOnly` de la instrucción `Dim` que declara la variable o quite la instrucción que le asigna un valor.  
  
## Vea también  
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)