---
title: Gráfico de utilización de la CPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8058995c8ae45c40f202aaa1e788891da3eb985d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180494"
---
# <a name="cpu-utilization-graph"></a>Gráfico de utilización de la CPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El gráfico de utilización de la CPU muestra el nivel de uso en una aplicación a lo largo del tiempo. El eje X representa la duración de la traza y el eje Y representa el número de núcleos lógicos del sistema. El gráfico no muestra qué núcleo concreto está activo en un momento dado. Por ejemplo, si dos núcleos se ejecutan al 50 por ciento de su capacidad durante un período de tiempo determinado, esta vista muestra que se está utilizando un núcleo lógico.  
  
## <a name="cpu-utilization-graph-colors"></a>Colores del gráfico de utilización de la CPU  
  
- El color verde indica el uso de núcleos lógicos del sistema por parte del proceso actual.  
  
- El color gris claro indica el uso de núcleos lógicos por parte de otros procesos en el sistema. Un alto porcentaje de color gris claro en el gráfico de la CPU indica que el sistema está muy cargado por otros procesos que es probable que tengan preferencia sobre su proceso. Para reducir el consumo de núcleos lógicos por otros procesos, reduzca el número de los que se están ejecutando en el sistema.  
  
- El color gris oscuro indica el consumo de núcleos lógicos que hace el proceso del sistema. No puede controlar directamente esto, pero resulta útil saber cuándo se está produciendo porque puede afectar a la disponibilidad de núcleos lógicos para el proceso.  
  
- El color blanco indica la disponibilidad de núcleos lógicos no usados en el sistema. Estos núcleos están disponibles para su proceso si puede encontrar más oportunidades de paralelismo.  
  
## <a name="see-also"></a>Otras referencias  
 [Vista Utilización](../profiling/utilization-view.md)   
 [Uso medio de la CPU](../profiling/average-cpu-utilization.md)
