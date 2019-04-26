---
title: Seguimiento de archivos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7770da734143b2b6185b266137eeb46ba25bd32a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968072"
---
# <a name="file-tracking"></a>Seguimiento de archivos
Los registros de seguimiento de archivos llaman al sistema de archivos de Windows para un proceso y sus procesos secundarios. Para controlar cuándo activar y desactivar este registro y especificar el archivo de registro que se debe utilizar, los programas llaman a las funciones que se enumeran a continuación.

- [EndTrackingContext](../msbuild/endtrackingcontext.md) Detiene el seguimiento del contexto actual.

- [ResumeTracking](../msbuild/resumetracking.md) Reanuda el seguimiento después de una llamada a [SuspendTracking](../msbuild/suspendtracking.md).

- [SetThreadCount](../msbuild/setthreadcount.md) Establece el número de subprocesos que se utilizarán para el seguimiento.

- [StartTrackingContext](../msbuild/starttrackingcontext.md) Inicia un nuevo contexto de seguimiento.

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) Inicia un nuevo contexto de seguimiento con la raíz especificada.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) Finaliza el seguimiento y libera los recursos utilizados.

- [SuspendTracking](../msbuild/suspendtracking.md) Suspende el seguimiento temporalmente.

- [WriteAllTLogs](../msbuild/writealltlogs.md) Escribe los registros de seguimiento para todos los contextos.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) Escribe el registro de seguimiento del contexto actual.