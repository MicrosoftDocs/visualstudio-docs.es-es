---
title: Seguimiento de archivos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 98bf98493d6f45be31ef98ae0b4a98bfbd66e402
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="file-tracking"></a>Seguimiento de archivos
Los registros de seguimiento de archivos llaman al sistema de archivos de Windows para un proceso y sus procesos secundarios. Para controlar cuándo activar y desactivar este registro y especificar el archivo de registro que se debe utilizar, los programas llaman a las funciones que se enumeran a continuación.  
  
## <a name="in-this-section"></a>En esta sección  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Detiene el seguimiento del contexto actual.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Reanuda el seguimiento después de una llamada a [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Establece el número de subprocesos que se utilizarán para el seguimiento.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Inicia un nuevo contexto de seguimiento.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Inicia un nuevo contexto de seguimiento con la raíz especificada.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Finaliza el seguimiento y libera los recursos utilizados.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Suspende el seguimiento temporalmente.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Escribe los registros de seguimiento para todos los contextos.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Escribe el registro de seguimiento del contexto actual.