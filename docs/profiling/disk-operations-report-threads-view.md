---
title: "Informe de operaciones de disco (Vista de subprocesos) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.diskoperations"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, informe de operaciones de archivo (Vista de subprocesos)"
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Informe de operaciones de disco (Vista de subprocesos)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El informe de las operaciones de disco muestra operaciones de E\/S de disco de los canales de disco.  
  
 Para cada acceso de disco que se realiza en nombre del proceso del que se está generando el perfil en la ventana visible actualmente, se muestra esta información:  
  
-   El nombre y PID de proceso que realizó el acceso a disco.  
  
-   El identificador del subproceso que obtuvo acceso a disco.  
  
-   Nombre del archivo al que se obtuvo acceso.  
  
-   El número de lecturas por archivo  
  
-   El número de bytes leídos.  
  
-   La latencia de lectura, en milisegundos.  
  
-   El número de escrituras.  
  
-   El número de bytes escritos.  
  
-   La latencia de escritura, en milisegundos.  
  
## Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)