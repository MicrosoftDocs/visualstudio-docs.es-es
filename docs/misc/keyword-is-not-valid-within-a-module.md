---
title: "&#39;&lt;keyword&gt;&#39; no es v&#225;lido dentro de un m&#243;dulo. | Microsoft Docs"
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
  - "vbc32001"
  - "bc32001"
helpviewer_keywords: 
  - "BC32001"
ms.assetid: b00757ac-5652-460d-9d2c-11b264d7ec7f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;keyword&gt;&#39; no es v&#225;lido dentro de un m&#243;dulo.
Se usa una palabra clave relacionada con las instancias de clase, como `Me` o `MyBase`, dentro de un módulo. Los módulos no tienen herencia ni instancias.  
  
 **Identificador de error:** BC32001  
  
### Para corregir este error  
  
-   Si el código que utiliza la palabra clave involucra instancias de clases, muévalo a una implementación de la clase.  
  
-   Si el código que utiliza la palabra clave se aplica al módulo, quite la palabra clave no válida.  
  
## Vea también  
 [Me](http://msdn.microsoft.com/es-es/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyBase \- delete](http://msdn.microsoft.com/es-es/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)