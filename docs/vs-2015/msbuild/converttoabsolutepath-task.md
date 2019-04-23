---
title: Tarea ConvertToAbsolutePath | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ConvertToAbsolutePath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ConvertToAbsolutePath task [MSBuild]
- MSBuild, ConvertToAbsolutePath task
ms.assetid: f1af2cb8-b4ef-4a72-be80-22fa526c4491
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 399ffeae65ba935e3682b54eff5ee1b0b687aa9d
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667734"
---
# <a name="converttoabsolutepath-task"></a>ConvertToAbsolutePath (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Convierte una ruta de acceso relativa o una referencia en una ruta de acceso absoluta.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la tarea `ConvertToAbsolutePath`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Paths`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Lista de rutas de acceso relativas que se convertirán en rutas de acceso absolutas.|  
|`AbsolutePaths`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Lista de rutas de acceso absolutas de los elementos que se han pasado.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
