---
title: Vista Núcleos | Microsoft Docs
description: Obtenga más detalles sobre la información proporcionada por la vista Núcleos. Puede ayudarle a utilizar la afinidad de subprocesos o la administración de grupos de subprocesos para optimizar el rendimiento de la memoria caché.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b124cc2f609ab7a113fd28f7086172169138d5f
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720714"
---
# <a name="cores-view"></a>Vista de núcleos
**Vista de núcleos** muestra cómo se asignó la ejecución de los subprocesos a los núcleos del procesador lógico (elija **Analizar** > **Visualizador de simultaneidad** para iniciar el visualizador de simultaneidad). Si está escribiendo aplicaciones de servidor, esta vista puede ayudarlo a optimizar el rendimiento de la memoria caché mediante el uso de administración de grupos de subprocesos o de afinidad de subprocesos. También puede ayudarlo a examinar los casos en que el uso de la afinidad de subprocesos puede haber empeorado el problema de la migración entre núcleos. La vista Núcleos tiene dos partes: un gráfico y una leyenda.

 El gráfico muestra los núcleos lógicos en el eje Y y el tiempo en el eje X. Cada subproceso del gráfico tiene un color único para que pueda seguir su movimiento entre núcleos a lo largo del tiempo. Puede filtrar los subprocesos de este gráfico si los selecciona en el área de la leyenda.

 El área de la leyenda tiene una entrada para cada color del gráfico. Cada entrada muestra el color y el nombre del subproceso, el número de cambios de contexto entre núcleos, el número total de cambios de contexto y el porcentaje de cambios de contexto que atraviesan núcleos. La leyenda se ordena por el número de cambios de contexto entre núcleos, en orden decreciente. Enumera únicamente los subprocesos ejecutados durante el intervalo de tiempo mostrado.  La lista se actualiza si hace zoom o un movimiento panorámico.

## <a name="see-also"></a>Consulte también
- [Visualizador de simultaneidad](../profiling/concurrency-visualizer.md)
- [Vista de utilización](../profiling/utilization-view.md)
- [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)