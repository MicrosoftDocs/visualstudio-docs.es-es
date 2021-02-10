---
title: Gráfico de utilización de la CPU | Microsoft Docs
description: Obtenga más información sobre el gráfico de utilización de la CPU, que muestra el nivel de uso en una aplicación a lo largo del tiempo. El uso se muestra como el número de núcleos lógicos en uso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5ec57ac6601557bf644c818822fea70a296fd0c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956014"
---
# <a name="cpu-utilization-graph"></a>Gráfico de uso de la CPU
El gráfico de utilización de la CPU muestra el nivel de uso en una aplicación a lo largo del tiempo. El eje X representa la duración de la traza y el eje Y representa el número de núcleos lógicos del sistema. El gráfico no muestra qué núcleo concreto está activo en un momento dado. Por ejemplo, si dos núcleos se ejecutan al 50 por ciento de su capacidad durante un período de tiempo determinado, esta vista muestra que se está utilizando un núcleo lógico.

## <a name="cpu-utilization-graph-colors"></a>Colores del gráfico de utilización de la CPU

- El color verde indica el uso de núcleos lógicos del sistema por parte del proceso actual.

- El color gris claro indica el uso de núcleos lógicos por parte de otros procesos en el sistema. Un alto porcentaje de color gris claro en el gráfico de la CPU indica que el sistema está muy cargado por otros procesos y que es probable que tengan preferencia sobre su proceso. Para reducir el consumo de núcleos lógicos por otros procesos, reduzca el número de los que se están ejecutando en el sistema.

- El color gris oscuro indica el consumo de núcleos lógicos que hace el proceso del sistema. No puede controlar directamente esto, pero resulta útil saber cuándo se está produciendo porque puede afectar a la disponibilidad de núcleos lógicos para el proceso.

- El color blanco indica la disponibilidad de núcleos lógicos no usados en el sistema. Estos núcleos están disponibles para su proceso si puede encontrar más oportunidades de paralelismo.

## <a name="see-also"></a>Consulte también
- [Vista de utilización](../profiling/utilization-view.md)
- [Uso medio de la CPU](../profiling/average-cpu-utilization.md)