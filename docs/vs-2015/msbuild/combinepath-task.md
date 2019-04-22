---
title: CombinePath (Tarea) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b97714fc707d8f9174a01dcc1fe7b3b59176de2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651584"
---
# <a name="combinepath-task"></a>CombinePath (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Combina las rutas de acceso especificadas en una única ruta de acceso.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la [tarea CombinePath](../msbuild/combinepath-task.md).  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`BasePath`|Parámetro `String` requerido.<br /><br /> Ruta de acceso base que se combinará con las demás rutas de acceso. Puede ser una ruta de acceso relativa, una ruta de acceso absoluta o estar en blanco.|  
|`Paths`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Una lista de rutas de acceso individuales que se combinarán con el elemento BasePath para formar la ruta de acceso combinada. Las rutas acceso pueden ser relativas o absolutas.|  
|`CombinedPaths`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> La ruta de acceso combinada que se crea mediante la tarea.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
