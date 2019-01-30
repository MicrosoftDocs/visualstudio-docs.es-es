---
title: ResolveManifestFiles (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ResolveManifestFiles task [MSBuild]
- MSBuild, ResolveManifestFiles task
ms.assetid: e1e14f67-9b69-433f-94d4-a783a68676b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e3d5fd327e6ef9db5029697d502d27574a8a8f7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043224"
---
# <a name="resolvemanifestfiles-task"></a>ResolveManifestFiles (tarea)
Resuelve los siguientes elementos en el proceso de compilación de los archivos para la generación de manifiestos: elementos compilados, dependencias, ensamblados satélite, contenido, símbolos de depuración y documentación.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `ResolveManifestFiles` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`DeploymentManifestEntryPoint`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el nombre del manifiesto de implementación.|  
|`EntryPoint`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el ensamblado administrado o la referencia de manifiesto ClickOnce que es el punto de entrada para el manifiesto.|  
|`ExtraFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los archivos adicionales.|  
|`ManagedAssemblies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los ensamblados administrados.|  
|`NativeAssemblies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los ensamblados nativos.|  
|`OutputAssemblies`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los ensamblados generados.|  
|`OutputDeploymentManifestEntryPoint`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el punto de entrada del manifiesto de implementación de salida.|  
|`OutputEntryPoint`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el punto de entrada de la salida.|  
|`OutputFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los archivos de salida.|  
|`PublishFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los archivos de publicación.|  
|`SatelliteAssemblies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los ensamblados satélite.|  
|`SigningManifests`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se firman los manifiestos.|  
|`TargetCulture`|Parámetro `String` opcional.<br /><br /> Especifica la referencia cultural de destino para los ensamblados satélite.|  
|`TargetFrameworkVersion`|Parámetro `String` opcional.<br /><br /> Especifica la versión de .NET Framework de destino.|  
  
## <a name="remarks"></a>Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)