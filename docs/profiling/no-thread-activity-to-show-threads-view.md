---
title: "No hay actividades de subprocesos que mostrar (Vista de subprocesos) | Microsoft Docs"
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
  - "vs.cv.threads.nothreadreport"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, No hay actividades de subprocesos que mostrar (Vista de subprocesos)"
ms.assetid: aa5ae9d0-561d-4ef8-b36b-258ce553d50a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# No hay actividades de subprocesos que mostrar (Vista de subprocesos)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta área muestra datos acerca de los subprocesos no ocultos del intervalo de tiempo visible en este momento.  
  
 Si no hay información visible, compruebe los siguientes valores:  
  
-   ¿El nivel de la ampliación es alto?  Intente alejar o desplazar la imagen para que haya más actividad de subprocesos dentro del alcance.  
  
-   ¿Hay demasiados subprocesos ocultos?  En ese caso, intente mostrar todos los subprocesos  
  
-   Si **Solo mi código** está seleccionado, solamente puede ver los datos de su propio código.  Intente desactivar la opción para determinar si hay actividad de subprocesos del sistema.  
  
-   Asegúrese de que la Reducción de nodos irrelevantes está establecida en un umbral bajo.  
  
## Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)