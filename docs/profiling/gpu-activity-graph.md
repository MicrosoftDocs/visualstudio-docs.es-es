---
title: Gráfico de actividad de GPU | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5734b9eb1b4307f7c32dcb8a170f7c6c571f46ca
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617566"
---
# <a name="gpu-activity-graph"></a>Gráfico de actividad de GPU
El gráfico de actividad de GPU en el visualizador de simultaneidad muestra el nivel de actividad de DirectX en el sistema, medido por el número de motores de DirectX que se utilizan con el tiempo.  El gráfico no muestra qué motores específicos se utilizaron.  Se considera que un motor está en uso si está procesando cualquier trabajo de GPU.

## <a name="gpu-activity-graph-colors"></a>Colores del gráfico de actividad de GPU
 El color verde indica el consumo de los motores de DirectX que hace el proceso actual.

 El color gris claro indica el consumo de motores de DirectX que hacen otros procesos en el sistema. Para reducir el consumo de motores de DirectX que hacen otros procesos, reduzca el número de los demás procesos que se están ejecutando en el sistema.

 El color blanco indica la disponibilidad de los motores de DirectX no utilizados en el sistema. Estos motores están disponibles para su proceso si puede encontrar más oportunidades de explotarlos. Algunos motores solo pueden utilizarse para determinados tipos de tareas.

## <a name="see-also"></a>Vea también
- [Vista Utilización](../profiling/utilization-view.md)