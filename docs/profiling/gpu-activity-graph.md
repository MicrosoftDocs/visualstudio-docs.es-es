---
title: Gráfico de actividad de GPU | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9dcadfdbfa52815fdd6d88f78afb88d421e203c7
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237915"
---
# <a name="gpu-activity-graph"></a>Gráfico de actividad de GPU
El gráfico de actividad de GPU en el visualizador de simultaneidad muestra el nivel de actividad de DirectX en el sistema, medido por el número de motores de DirectX que se utilizan con el tiempo.  El gráfico no muestra qué motores específicos se utilizaron.  Se considera que un motor está en uso si está procesando cualquier trabajo de GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Colores del gráfico de actividad de GPU  
 El color verde indica el consumo de los motores de DirectX que hace el proceso actual.  
  
 El color gris claro indica el consumo de motores de DirectX que hacen otros procesos en el sistema. Para reducir el consumo de motores de DirectX que hacen otros procesos, reduzca el número de los demás procesos que se están ejecutando en el sistema.  
  
 El color blanco indica la disponibilidad de los motores de DirectX no utilizados en el sistema. Estos motores están disponibles para su proceso si puede encontrar más oportunidades de explotarlos. Algunos motores solo pueden utilizarse para determinados tipos de tareas.  
  
## <a name="see-also"></a>Vea también  
 [Vista Utilización](../profiling/utilization-view.md)