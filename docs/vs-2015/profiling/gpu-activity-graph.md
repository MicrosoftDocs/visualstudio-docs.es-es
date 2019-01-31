---
title: Gráfico de actividad de GPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4546c3be480349f3e2cb36f483fa8711bc2ac49
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769052"
---
# <a name="gpu-activity-graph"></a>Gráfico de actividad de GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El gráfico de actividad de GPU en el visualizador de simultaneidad muestra el nivel de actividad de DirectX en el sistema, medido por el número de motores de DirectX que se utilizan con el tiempo.  El gráfico no muestra qué motores específicos se utilizaron.  Se considera que un motor está en uso si está procesando cualquier trabajo de GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Colores del gráfico de actividad de GPU  
 El color verde indica el consumo de los motores de DirectX que hace el proceso actual.  
  
 El color gris claro indica el consumo de motores de DirectX que hacen otros procesos en el sistema. Para reducir el consumo de motores de DirectX que hacen otros procesos, reduzca el número de los demás procesos que se están ejecutando en el sistema.  
  
 El color blanco indica la disponibilidad de los motores de DirectX no utilizados en el sistema. Estos motores están disponibles para su proceso si puede encontrar más oportunidades de explotarlos. Algunos motores solo pueden utilizarse para determinados tipos de tareas.  
  
## <a name="see-also"></a>Vea también  
 [Vista de uso](../profiling/utilization-view.md)
