---
title: Segmento de escala de tiempo vacío | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad8d87c0574ac2c7671012fff6a81a568d6bff5f
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34764535"
---
# <a name="empty-timeline-segment"></a>Segmento de escala de tiempo vacío
En el visualizador de simultaneidad, el motivo por el que una sección de la escala de tiempo está vacía (tiene un fondo blanco) depende del tipo de canal.  
  
-   Un canal de subproceso de CPU, significa que el subproceso no existió durante esta parte de la escala de tiempo. Si está interesado en el subproceso, puede encontrar su sección en ejecución mediante el control de zoom o el desplazamiento horizontal.  
  
-   Para un canal de E/S, significa que no se ha producido ningún acceso al disco en nombre del proceso de destino en ese momento.  
  
-   Para un canal de DirectX, significa que no se ha realizado ningún trabajo de GPU en nombre del proceso de destino durante esta parte de la escala de tiempo.  
  
-   Un canal de marcador, significa que no se generó ningún marcador.  
  
## <a name="see-also"></a>Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)   
 [Control de zoom (vista Subprocesos)](../profiling/zoom-control-threads-view.md)