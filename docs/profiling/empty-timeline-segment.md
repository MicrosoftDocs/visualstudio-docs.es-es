---
title: "Segmento de escala de tiempo vac&#237;o | Microsoft Docs"
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
  - "vs.cv.threads.timeline.empty"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, segmento de escala de tiempo vacío"
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Segmento de escala de tiempo vac&#237;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En el Visualizador de simultaneidad, el motivo para que una sección de la escala de tiempo esté vacía \(tiene un fondo blanco\) depende del tipo de canal.  
  
-   Para un canal de subproceso CPU, significa que el subproceso no ha existido durante una parte de la escala de tiempo.  Si está interesado en el subproceso, puede encontrar su sección en ejecución utilizando el zoom o la barra de desplazamiento horizontal.  
  
-   Para un canal I\/O, significa que no ha ocurrido ningún acceso de disco en nombre del proceso de destino en ese momento.  
  
-   Para un canal de DirectX, significa que no se ha realizado ningún trabajo GPU en nombre del proceso de destino durante una parte de la escala de tiempo.  
  
-   Para un canal de marcador, significa que no se generaron marcadores.  
  
## Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)   
 [Zoom \(control\) \(Vista de subprocesos\)](../profiling/zoom-control-threads-view.md)