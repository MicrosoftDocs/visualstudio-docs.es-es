---
title: "La interfaz &#39;&lt;interfacename&gt;&#39; no se puede indizar porque no tiene ninguna propiedad predeterminada | Microsoft Docs"
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
  - "bc30547"
  - "vbc30547"
helpviewer_keywords: 
  - "BC30547"
ms.assetid: d9d83868-5e81-4ec5-878e-2303489d8f2f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La interfaz &#39;&lt;interfacename&gt;&#39; no se puede indizar porque no tiene ninguna propiedad predeterminada
Las expresiones de índice deben dar como resultado un valor cuyo tipo es una matriz, un valor cuyo tipo tiene un conjunto de propiedades predeterminadas sobrecargadas o un conjunto de propiedades sobrecargadas. Una interfaz solo puede tener un método o propiedad predeterminados. Esto significa que puede heredar una interfaz que contiene un método o propiedad predeterminados, o bien su bloque de definición puede contener un método o propiedad marcada como predeterminada.  
  
 **Identificador de error:** BC30547  
  
### Para corregir este error  
  
-   Proporcione una propiedad predeterminada en la interfaz.  
  
## Vea también  
 [Interface \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/interface-statement)