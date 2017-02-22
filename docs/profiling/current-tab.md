---
title: "Pesta&#241;a actual | Microsoft Docs"
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
  - "vs.cv.threads.reportnav.current"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, pila de llamadas en el punto de selección"
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pesta&#241;a actual
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Al hacer clic en la pestaña **Actual**, se puede ver una pila de llamadas \(si está disponible\) que está más cerca del punto de selección actual en la línea de tiempo si se selecciona un segmento de un subproceso de la CPU.  En este caso, el punto de selección se representa mediante una flecha negra o un símbolo de intercalación, sobre la línea de tiempo.  Cuando se selecciona un segmento de bloqueo, no se muestra el símbolo de intercalación porque no ha habido ejecución.  Sin embargo, el segmento se mantiene resaltado y se muestra una pila de llamadas.  
  
 La pestaña **Actual** también muestra información sobre segmentos de actividades de DirectX, los marcadores y el acceso de E\/S.  Para los segmentos de actividad de DirectX, se muestra información sobre la manera en que se procesan los paquetes de DMA en la cola de hardware.  Para los marcadores, se muestra información sobre la descripción y el tipo de marcador.  Para el acceso de E\/S, se muestra información sobre el archivo y el número de bytes leídos o escritos.  
  
## Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)