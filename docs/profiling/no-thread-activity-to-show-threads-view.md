---
title: No hay actividades de subprocesos que mostrar (Vista de subprocesos) | Microsoft Docs
description: Obtenga más información sobre la vista de subprocesos, en la que no hay ninguna actividad que mostrar en el intervalo de tiempo visible actualmente.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.nothreadreport
helpviewer_keywords:
- Concurrency Visualizer, No Thread Activity to Show (Threads View)
ms.assetid: aa5ae9d0-561d-4ef8-b36b-258ce553d50a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27298b03a03edf99a12a6d067a22ca8ba17faef0
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722885"
---
# <a name="no-thread-activity-to-show-threads-view"></a>No hay actividades de subprocesos que mostrar (vista de subprocesos)
En esta área se muestran datos sobre los subprocesos que no están ocultos en el intervalo de tiempo visible actualmente.

 Si no hay información visible, compruebe esta configuración:

- ¿El nivel de zoom es alto? Intente alejar o desplazar para mostrar mayor cantidad de la actividad de los subprocesos.

- ¿Hay demasiados subprocesos ocultos? Si es así, intente mostrar todos los subprocesos

- Si está seleccionado **Solo mi código**, solo puede ver datos sobre su código. Pruebe a desactivar la opción para determinar si hay alguna actividad del subproceso del sistema.

- Asegúrese de que Reducción de nodos irrelevantes está establecida en un umbral bajo.

## <a name="see-also"></a>Vea también
- [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)