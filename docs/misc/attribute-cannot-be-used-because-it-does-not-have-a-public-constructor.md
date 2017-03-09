---
title: "No se puede usar el atributo porque no tiene un constructor Public. | Microsoft Docs"
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
  - "vbc30758"
  - "bc30758"
helpviewer_keywords: 
  - "BC30758"
ms.assetid: b72d1ff2-f6b2-4a89-9ac2-8765f77bcc97
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede usar el atributo porque no tiene un constructor Public.
El constructor del atributo usado es `Private`, y no se puede usar.  
  
 **Identificador de error:** BC30758  
  
### Para corregir este error  
  
1.  Si ve este error con un atributo personalizado que ha desarrollado, cambie el modificador de acceso del constructor `Sub``New` a `Public`.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos en Visual Basic](http://msdn.microsoft.com/es-es/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Duración de los objetos: cómo se crean y destruyen](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)