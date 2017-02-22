---
title: "Seguimiento de archivos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, seguimiento de archivos"
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Seguimiento de archivos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los registros de seguimiento de archivos llaman al sistema de archivos de Windows para un proceso y sus procesos secundarios.  Para controlar cuándo activar y desactivar este registro y especificar el archivo de registro que se debe utilizar, los programas llaman a las funciones que se enumeran a continuación.  
  
## En esta sección  
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