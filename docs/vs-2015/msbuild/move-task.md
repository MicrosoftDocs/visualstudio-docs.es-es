---
title: Tarea Move | Microsoft Docs
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
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2919d139e48f6e08845dc3990b0df5a8591283c0
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54791386"
---
# <a name="move-task"></a>Move (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Mueve los archivos a una nueva ubicación.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Move`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`DestinationFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica la lista de archivos en la que se moverán los archivos de código fuente. Se espera que esta lista sea una asignación unívoca a la lista especificada en el parámetro `SourceFiles`. Es decir, el primer archivo especificado en `SourceFiles` se moverá a la primera ubicación especificada en `DestinationFiles`, etc.|  
|`DestinationFolder`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el directorio en el que se desea mover los archivos.|  
|`MovedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los elementos que se movieron correctamente.|  
|`OverwriteReadOnlyFiles`|Parámetro `Boolean` opcional.<br /><br /> Si `true`, se sobrescriben los archivos aunque estén marcados como archivos de solo lectura.|  
|`SourceFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos que se van a mover.|  
  
## <a name="remarks"></a>Comentarios  
 Se debe especificar el parámetro `DestinationFolder` o `DestinationFiles`, pero no ambos. Si se especifican los dos, la tarea produce un error y se registra un error.  
  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
