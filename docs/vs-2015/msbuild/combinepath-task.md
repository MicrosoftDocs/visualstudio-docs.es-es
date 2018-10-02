---
title: CombinePath (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: c3a7aba3111a799b650b7b3f7014d6d1a9f040b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568109"
---
# <a name="combinepath-task"></a>CombinePath (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CombinePath (tarea)](https://docs.microsoft.com/visualstudio/msbuild/combinepath-task).  
  
  
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



