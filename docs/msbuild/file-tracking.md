---
title: Seguimiento de archivos | Microsoft Docs
description: Use las funciones de seguimiento de archivos de MSBuild para registrar las llamadas al sistema de archivos de Windows para un proceso y sus procesos secundarios.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d61c3478515f2c8fa867666e6ff4ff72a0d4e65b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877127"
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
