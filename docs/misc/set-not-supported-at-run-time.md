---
title: "No se admite Set en tiempo de ejecuci&#243;n | Microsoft Docs"
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
  - "vbrID382"
ms.assetid: cb7285d3-778f-423d-a2be-88573be8ad48
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se admite Set en tiempo de ejecuci&#243;n
Se intentó establecer o cambiar una propiedad cuyo valor solo se puede establecer en tiempo de diseño.  
  
### Para corregir este error  
  
1.  Quite la referencia a la propiedad del código.  
  
2.  Cambie la referencia para que solo devuelva el valor de la propiedad en tiempo de ejecución.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Procedimiento: modificar las propiedades y los valores de configuración del proyecto](http://msdn.microsoft.com/es-es/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)