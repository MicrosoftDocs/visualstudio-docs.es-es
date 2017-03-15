---
title: "Omitiendo la opci&#243;n /noconfig porque se especific&#243; en un archivo de respuesta | Microsoft Docs"
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
  - "vbc2025"
  - "bc2025"
helpviewer_keywords: 
  - "BC2025"
ms.assetid: 87fb393d-e17f-4e50-8d98-d9dfeba30c3e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Omitiendo la opci&#243;n /noconfig porque se especific&#243; en un archivo de respuesta
La opción `/noconfig` indica al compilador que no compile con el archivo Vbc.rsp. Sin embargo, el compilador procesa el archivo Vbc.rsp antes de procesar los archivos de respuesta, por lo que el compilador no puede aceptar la opción `/noconfig` en un archivo de respuesta.  
  
 **Identificador de error:** BC2025  
  
### Para corregir este error  
  
1.  Quite la opción `/noconfig` del archivo de respuesta.  
  
2.  Especifique la opción `/noconfig` al invocar el compilador de línea de comandos.  
  
## Vea también  
 [\/noconfig](/dotnet/visual-basic/reference/command-line-compiler/noconfig)   
 [@ \(especificar archivo de respuesta\)](/dotnet/visual-basic/reference/command-line-compiler/specify-response-file)