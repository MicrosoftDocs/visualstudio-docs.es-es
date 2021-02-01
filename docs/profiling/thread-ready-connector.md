---
title: Conector listo para subprocesos | Microsoft Docs
description: Obtenga más información sobre el hecho de que, al hacer clic en un segmento de bloqueo para ver una pila de llamadas y su pila de desbloqueo, también puede aparecer el conector preparado para subprocesos.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.threadready
helpviewer_keywords:
- Concurrency Visualizer, Thread Ready
ms.assetid: 68e1ec38-4b10-4b01-b32f-6c9a00b2443c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 789c60be4f31d053c4ff9f95121bf8f0e0d4689e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718790"
---
# <a name="thread-ready-connector"></a>Conector listo para subprocesos
Al hacer clic en un segmento de bloqueo para ver una pila de llamadas y su pila de desbloqueo, también puede aparecer el conector preparado para subprocesos. Si el evento de desbloqueo se produjo en otro subproceso del proceso actual, el conector preparado para subprocesos identifica visualmente el subproceso y el segmento de ejecución que permitieron que el subproceso bloqueado reanudara la ejecución.