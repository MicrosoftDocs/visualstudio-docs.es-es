---
title: "La restricci&#243;n de tipo no puede ser una clase &#39;NotInheritable&#39; | Microsoft Docs"
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
  - "vbc32060"
  - "bc32060"
helpviewer_keywords: 
  - "BC32060"
ms.assetid: f45cc0b6-7df1-462a-b3df-c526c143e16a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La restricci&#243;n de tipo no puede ser una clase &#39;NotInheritable&#39;
Una lista de restricciones incluye una clase marcada como [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable).  
  
 Una lista de restricciones en un parámetro de tipo puede aceptar como máximo una clase. Un argumento de tipo proporcionado para ese parámetro de tipo debe heredar de esa clase. Por lo tanto, el parámetro de tipo no puede aceptar una clase *sealed*, o `NotInheritable`, como una restricción.  
  
 **Identificador de error:** BC32060  
  
### Para corregir este error  
  
-   Si el parámetro de tipo debe ser capaz de heredar de la clase y tiene control sobre la definición de la clase, quite la declaración `NotInheritable` de la clase.  
  
-   Si la clase debe seguir siendo `NotInheritable`, no puede usarla como una restricción. Quite el nombre de clase de la lista de restricciones.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)