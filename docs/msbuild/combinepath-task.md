---
title: CombinePath (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2e380c6207b3f59b1717ebff6f17261acc7ee52
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37946786"
---
# <a name="combinepath-task"></a>CombinePath (tarea)
Combina las rutas de acceso especificadas en una única ruta de acceso.  
  
## <a name="task-parameters"></a>Parámetros de la tarea  
 En la siguiente tabla se describen los parámetros de [CombinePath (Tarea)](../msbuild/combinepath-task.md).  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`BasePath`|Parámetro `String` requerido.<br /><br /> Ruta de acceso base que se combinará con las demás rutas de acceso. Puede ser una ruta de acceso relativa, una ruta de acceso absoluta o estar en blanco.|  
|`Paths`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Una lista de rutas de acceso individuales que se combinarán con el elemento BasePath para formar la ruta de acceso combinada. Las rutas acceso pueden ser relativas o absolutas.|  
|`CombinedPaths`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> La ruta de acceso combinada que se crea mediante la tarea.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension (Clase base)](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)