---
title: Tiempo de ejecución (vista de subprocesos) | Microsoft Docs
description: Revise el tiempo de ejecución en la vista Threads (Subprocesos) del visualizador de simultaneidad. El tiempo de ejecución se representa mediante segmentos que muestran cuando un subproceso está funcionando activamente en un núcleo lógico.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5c62c57e3037b38c2729917d2b882550b9c2d126
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861613"
---
# <a name="execution-time-threads-view"></a>Tiempo de ejecución (vista de subprocesos)
Estos segmentos de la escala de tiempo de la vista de subprocesos representan el tiempo de ejecución, cuando el subproceso está realizando activamente una tarea en un núcleo lógico en el sistema.

 Los cambios en el estado del subproceso se detectan mediante eventos de cambio de contexto de kernel. El seguimiento de eventos para Windows (ETW) captura pilas de muestras cada milisegundo. En un segmento verde muy corto, es posible que no se tome ninguna muestra. Por lo tanto, puede que algunos segmentos de ejecución cortos no muestren ninguna pila de llamadas.

 Al hacer clic en un segmento de ejecución, el visualizador de simultaneidad muestra la pila de muestras más cercana a la ubicación del clic. La ubicación de esa pila de muestras se indica mediante una flecha negra, o un símbolo de intercalación, sobre la escala de tiempo y la pila de muestras aparece en la pestaña **Actual**.

 Para ver un perfil de muestreo tradicional para todos los segmentos de ejecución en la vista actual, haga clic en **Ejecución** en el perfil de escala de tiempo visible.

## <a name="see-also"></a>Consulte también
- [Informe del perfil de ejecución](../profiling/execution-profile-report.md)
- [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)