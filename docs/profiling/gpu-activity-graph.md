---
title: Gráfico de actividad de GPU | Microsoft Docs
description: Entienda el gráfico GPU Activity (Actividad de GPU), que muestra el nivel de actividad de DirectX del sistema en el visualizador de simultaneidad.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 46f3e4ce7f155679bc3c701af90ff51e0fb20239
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907273"
---
# <a name="gpu-activity-graph"></a>Gráfico de actividad de GPU
El gráfico de actividad de GPU en el visualizador de simultaneidad muestra el nivel de actividad de DirectX en el sistema, medido por el número de motores de DirectX que se utilizan con el tiempo.  El gráfico no muestra qué motores específicos se utilizaron.  Se considera que un motor está en uso si está procesando cualquier trabajo de GPU.

## <a name="gpu-activity-graph-colors"></a>Colores del gráfico de actividad de GPU
 El color verde indica el consumo de los motores de DirectX que hace el proceso actual.

 El color gris claro indica el consumo de motores de DirectX que hacen otros procesos en el sistema. Para reducir el consumo de motores de DirectX que hacen otros procesos, reduzca el número de los demás procesos que se están ejecutando en el sistema.

 El color blanco indica la disponibilidad de los motores de DirectX no utilizados en el sistema. Estos motores están disponibles para su proceso si puede encontrar más oportunidades de explotarlos. Algunos motores solo pueden utilizarse para determinados tipos de tareas.

## <a name="see-also"></a>Consulte también
- [Vista de utilización](../profiling/utilization-view.md)