---
title: Segmento de escala de tiempo vacío | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ac39a776cb7e6c2c9cbce648c0b3ca3ebc86783
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770750"
---
# <a name="empty-timeline-segment"></a>Segmento de escala de tiempo vacío
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el visualizador de simultaneidad, el motivo por el que una sección de la escala de tiempo está vacía (tiene un fondo blanco) depende del tipo de canal.  
  
-   Un canal de subproceso de CPU, significa que el subproceso no existió durante esta parte de la escala de tiempo. Si está interesado en el subproceso, puede encontrar su sección en ejecución mediante el control de zoom o el desplazamiento horizontal.  
  
-   Para un canal de E/S, significa que no se ha producido ningún acceso al disco en nombre del proceso de destino en ese momento.  
  
-   Para un canal de DirectX, significa que no se ha realizado ningún trabajo de GPU en nombre del proceso de destino durante esta parte de la escala de tiempo.  
  
-   Un canal de marcador, significa que no se generó ningún marcador.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)   
 [Control de zoom (vista de subprocesos)](../profiling/zoom-control-threads-view.md)
