---
title: "No se puede especificar /win32icon y /win32resource | Microsoft Docs"
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
  - "vbc2023"
  - "bc2023"
helpviewer_keywords: 
  - "BC2023"
ms.assetid: 60914807-1fde-4fef-9c6f-6f4a62527eed
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede especificar /win32icon y /win32resource
Las opciones `/win32resource` y `/win32icon` son mutuamente excluyentes, porque ambas insertan información de iconos en el archivo de salida.  
  
 **Identificador de error:** BC2023  
  
### Para corregir este error  
  
-   Use solo la opción `/win32icon` para insertar un archivo .ico en el archivo de salida. Este archivo .ico representa el archivo de salida en el Explorador de Windows.  
  
     O bien  
  
-   Use solo la opción `/win32resource` para insertar un archivo de recursos de Win32 en el archivo de salida. Un recurso de Win32 puede contener información de versión o de mapa de bits de \(icono\) que ayuda a identifica la aplicación en el Explorador de Windows.  
  
## Vea también  
 [\/win32icon](/dotnet/visual-basic/reference/command-line-compiler/win32icon)   
 [\/win32resource](/dotnet/visual-basic/reference/command-line-compiler/win32resource)