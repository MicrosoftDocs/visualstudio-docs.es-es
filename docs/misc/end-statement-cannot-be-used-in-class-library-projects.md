---
title: "La instrucci&#243;n &#39;End&#39; no se puede usar en proyectos de bibliotecas de clase | Microsoft Docs"
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
  - "bc30615"
  - "vbc30615"
helpviewer_keywords: 
  - "BC30615"
ms.assetid: c8606b17-b50b-4014-b76e-b748d57e9389
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;End&#39; no se puede usar en proyectos de bibliotecas de clase
Los proyectos de bibliotecas de clase que se utilizan para crear archivos DLL no permiten el uso de la palabra clave `End` para detener la ejecución de código en un procedimiento.  
  
 **Id. de error:** BC30615  
  
### Para corregir este error  
  
-   Utilice estructuras de control como `While` y `For` para controlar el flujo de ejecución del programa.  
  
## Vea también  
 [Flujo de control](/dotnet/visual-basic/programming-guide/language-features/control-flow/index)