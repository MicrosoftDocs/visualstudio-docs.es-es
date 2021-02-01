---
title: Tiempo de administración de la memoria | Microsoft Docs
description: Obtenga más información sobre cómo este escenario implica que un subproceso está bloqueado por un evento asociado a una operación de administración de memoria como la paginación.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23e1dd2868f5b29a12f3f54f46e5cb5833d270af
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721208"
---
# <a name="memory-management-time"></a>Tiempo de administración de la memoria
Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como Administración de memoria. Este escenario implica que un subproceso está bloqueado por un evento que está asociado a una operación de administración de memoria como la paginación. Durante este tiempo, un subproceso se ha bloqueado en una API o estado del kernel que el visualizador de simultaneidad está contando como administración de memoria. Esto incluye eventos como la paginación y la asignación de memoria.

 Examine las pilas de llamadas asociadas y los informes de perfil para entender mejor las razones subyacentes de los bloqueos que se clasifican como Administración de memoria.

## <a name="see-also"></a>Vea también
- [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)