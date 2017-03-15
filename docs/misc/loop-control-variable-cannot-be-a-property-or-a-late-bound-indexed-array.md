---
title: "La variable de control de un bucle no puede ser una propiedad ni una matriz indizada enlazada en tiempo de ejecuci&#243;n | Microsoft Docs"
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
  - "bc30039"
  - "vbc30039"
helpviewer_keywords: 
  - "BC30039"
ms.assetid: 63846449-b1df-4626-bf99-36fa9b187799
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable de control de un bucle no puede ser una propiedad ni una matriz indizada enlazada en tiempo de ejecuci&#243;n
La variable que se use para iterar en un bucle `For` debe ser de un tipo de datos numérico.  
  
 **Id. de error:** BC30039  
  
### Para corregir este error  
  
-   Cambie la declaración de la variable de control del bucle para especificar `Integer`, `Short`, `Long`, `Byte`, `Single`, `Double` o `Decimal`.  
  
## Vea también  
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)