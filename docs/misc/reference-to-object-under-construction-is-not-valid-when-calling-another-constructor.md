---
title: "La referencia a un objeto en construcci&#243;n no es v&#225;lida cuando se llama a otro constructor | Microsoft Docs"
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
  - "bc31095"
  - "vbc31095"
helpviewer_keywords: 
  - "BC31095"
ms.assetid: 68be49f1-e662-45c7-9998-e0006324535d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La referencia a un objeto en construcci&#243;n no es v&#225;lida cuando se llama a otro constructor
Se realizó una referencia a un miembro de objeto antes de que el constructor del objeto terminara de crearlo.  
  
 **Id. de error:** BC31095  
  
### Para corregir este error  
  
-   No use `MyBase`, `MyClass` ni `Me` al llamar a un constructor desde otro constructor.  
  
## Vea también  
 [Duración de los objetos: cómo se crean y destruyen](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)