---
title: "C&#243;mo: Cambiar la ubicaci&#243;n de binarios instrumentados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.binaries"
helpviewer_keywords: 
  - "binarios, instrumentados"
  - "instrumentación, binarios instrumentados"
  - "binarios instrumentados y cambio de ubicación"
  - "herramientas de generación de perfiles, binarios instrumentados"
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# C&#243;mo: Cambiar la ubicaci&#243;n de binarios instrumentados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durante la instrumentación, se insertan análisis en el binario para medir el rendimiento de la aplicación. Si opta por reubicar el binario instrumentado, se instrumenta una copia del binario original y se coloca en la ubicación especificada. Esta opción es útil si no desea que el generador de perfiles cambie el nombre del binario original. Si el binario no se reubica, se sobrescribe su versión original.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### Para reubicar un binario instrumentado  
  
1.  En el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
2.  En **Páginas de propiedades**, haga clic en las propiedades de **Binario**.  
  
3.  Active la casilla **Reubicar archivos binarios instrumentados**.  
  
4.  Especifique la ubicación del binario instrumentado.  
  
## Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)