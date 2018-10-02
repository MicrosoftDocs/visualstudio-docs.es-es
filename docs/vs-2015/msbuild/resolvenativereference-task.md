---
title: ResolveNativeReference (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d06171281706b2395cbac0c98b5b8a76c4da363c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566924"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ResolveNativeReference (tarea)](https://docs.microsoft.com/visualstudio/msbuild/resolvenativereference-task).  
  
  
Resuelve las referencias nativas. Implementa la clase <xref:Microsoft.Build.Tasks.ResolveNativeReference>. Esta clase es compatible con la infraestructura de .NET Framework que no está diseñada para utilizarse directamente desde el código.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la tarea `ResolveNativeReference`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`AdditionalSearchPaths`|[String] requerido (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->)`[]` parámetro.<br /><br /> Obtiene o establece las rutas de acceso de búsqueda para resolver identidades de ensamblado de las referencias nativas.|  
|`ContainedComComponents`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtiene o establece los componentes COM del ensamblado nativo.|  
|`ContainedLooseEtcFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtiene o establece los archivos Etc dinámicos que figuran en el manifiesto nativo.|  
|`ContainedLooseTlbFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtiene o establece los archivos .tlb dinámicos del ensamblado nativo.|  
|`ContainedPrerequisiteAssemblies`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtiene o establece los ensamblados que deben estar presentes para poder usar el manifiesto.|  
|`ContainedTypeLibraries`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtiene o establece las bibliotecas de tipos del ensamblado nativo.|  
|`ContainingReferenceFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Obtiene o establece los archivos de referencia.|  
|`NativeReferences`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Obtiene o establece las referencias de ensamblado nativas Win32.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



