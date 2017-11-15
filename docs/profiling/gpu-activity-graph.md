---
title: "Gráfico de actividad de GPU | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 964846b5a2cc06eaf03fa695e4f1c0aeb9efdca4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="gpu-activity-graph"></a>Gráfico de actividad de GPU
El gráfico de actividad de GPU en el visualizador de simultaneidad muestra el nivel de actividad de DirectX en el sistema, medido por el número de motores de DirectX que se utilizan con el tiempo.  El gráfico no muestra qué motores específicos se utilizaron.  Se considera que un motor está en uso si está procesando cualquier trabajo de GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Colores del gráfico de actividad de GPU  
 El color verde indica el consumo de los motores de DirectX que hace el proceso actual.  
  
 El color gris claro indica el consumo de motores de DirectX que hacen otros procesos en el sistema. Para reducir el consumo de motores de DirectX que hacen otros procesos, reduzca el número de los demás procesos que se están ejecutando en el sistema.  
  
 El color blanco indica la disponibilidad de los motores de DirectX no utilizados en el sistema. Estos motores están disponibles para su proceso si puede encontrar más oportunidades de explotarlos. Algunos motores solo pueden utilizarse para determinados tipos de tareas.  
  
## <a name="see-also"></a>Vea también  
 [Vista de uso](../profiling/utilization-view.md)