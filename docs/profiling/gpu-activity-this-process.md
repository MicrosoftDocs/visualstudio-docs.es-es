---
title: "Actividad GPU (Este proceso) | Microsoft Docs"
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
  - "vs.cv.threads.timeline.gpuexecution"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Actividad GPU (Este proceso)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los segmentos de **Actividad de la GPU \(este proceso\)** en la vista de subprocesos en el Visualizador de Simultaneidad representan ocasiones en las que la GPU estaba procesando solicitudes en nombre del proceso actual.  Estas solicitudes se envían a la GPU como paquetes de acceso directo a memoria \(DMA\).  La longitud de un segmento representa el tiempo que la GPU procesaba un paquete DMA en nombre del proceso actual.  
  
 Al seleccionar el segmento de la actividad de la GPU, el informe en la pestaña **Actual** muestra información sobre el paquete DMA que se procesó.  La información incluye la cantidad de tiempo que el paquete ha esperado en la cola de hardware asociada al motor de DirectX, el proceso que suministra el paquete, y el tiempo necesario para procesar el paquete.  Un proceso distinto del proceso actual pudo haber enviado físicamente el paquete DMA a la GPU.  El Visualizador de Simultaneidad puede detectar cuando otro proceso ha enviado trabajo a la GPU en nombre del proceso actual.