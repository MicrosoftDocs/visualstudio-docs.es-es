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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad3c913e6c983749e53940f5e75ad3bdba48bf92
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873637"
---
# <a name="memory-management-time"></a>Tiempo de administración de la memoria
Estos segmentos de la escala de tiempo están asociados a tiempos de bloqueo que se clasifican como Administración de memoria. Este escenario implica que un subproceso está bloqueado por un evento que está asociado a una operación de administración de memoria como la paginación. Durante este tiempo, un subproceso se ha bloqueado en una API o estado del kernel que el visualizador de simultaneidad está contando como administración de memoria. Esto incluye eventos como la paginación y la asignación de memoria.

 Examine las pilas de llamadas asociadas y los informes de perfil para entender mejor las razones subyacentes de los bloqueos que se clasifican como Administración de memoria.

## <a name="see-also"></a>Vea también
- [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)