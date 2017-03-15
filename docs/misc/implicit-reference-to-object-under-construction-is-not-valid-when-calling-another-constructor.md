---
title: "La referencia impl&#237;cita a un objeto en construcci&#243;n no es v&#225;lida al llamar a otro constructor. | Microsoft Docs"
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
  - "vbc31096"
  - "bc31096"
helpviewer_keywords: 
  - "BC31096"
ms.assetid: 558a2beb-aa5d-41a8-8655-ad3d16ac8acd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La referencia impl&#237;cita a un objeto en construcci&#243;n no es v&#225;lida al llamar a otro constructor.
Se realizó una referencia a un miembro de objeto antes de que el constructor de objetos terminara de construir el objeto.  
  
 **Identificador de error:** BC31096  
  
### Para corregir este error  
  
-   No use `MyBase`, `MyClass` ni `Me` al llamar a un constructor desde otro constructor.  
  
## Vea también  
 [Duración de los objetos: cómo se crean y destruyen](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)