---
title: "Actividad GPU (Otros procesos) | Microsoft Docs"
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
  - "vs.cv.threads.timeline.gpuother"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Actividad GPU (Otros procesos)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los segmentos de **Actividad de GPU \(de procesos\)** en la vista subprocesos del visualizador de simultaneidad representan ocasiones en que el GPU procesamiento solicitudes en nombre de otros procesos del sistema.  Estas solicitudes se envían a la GPU como paquetes de acceso directo a la memoria \(DMA\).  La longitud de un segmento representa el tiempo en que el paquete fue procesado por la GPU.  
  
 Al seleccionar esta clase de segmento, el informe en la pestaña **Actual** muestra información sobre el paquete que se procesó.  La información incluye la cantidad de tiempo que el paquete esperó en la cola de hardware asociada al motor de DirectX, el proceso que suministra el paquete y el tiempo necesario para procesar el paquete.