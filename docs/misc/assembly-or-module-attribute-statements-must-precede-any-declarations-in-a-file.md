---
title: "Las instrucciones de atributo Assembly o Module deben preceder cualquier declaraci&#243;n de un archivo | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30637"
  - "bc30637"
helpviewer_keywords: 
  - "BC30637"
ms.assetid: 80242581-fa8a-4903-9395-6f7ad1610231
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las instrucciones de atributo Assembly o Module deben preceder cualquier declaraci&#243;n de un archivo
Los atributos globales deben declararse al principio de un archivo de código fuente, después de las instrucciones `Option` y `Imports`, pero antes que cualquier otra instrucción.  
  
 **Identificador de error:** BC30637  
  
### Para corregir este error  
  
1.  Coloque los atributos globales, como `<Module:>` y `<Assembly:>` en la parte superior del archivo de código fuente.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Atributos en Visual Basic](http://msdn.microsoft.com/es-es/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [NO ESTÁ EN LA COMPILACIÓN: Atributos globales de Visual Basic](http://msdn.microsoft.com/es-es/253a32d8-1531-4504-b687-088554ab71d2)