---
title: Tarea ResolveNonMSBuildProjectOutput | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 1032afb19feff68e7a96dabcaa64eea79d6da34d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput (Tarea)
Determina los archivos de salida de las referencias de proyecto que no son de MSBuild.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `ResolveNonMSBuildProjectOutput` .  
  
|Parámetro|Description|  
|---------------|-----------------|  
|`PreresolvedProjectOutputs`|Parámetro `String` opcional.<br /><br /> Especifica una cadena XML que contiene resultados del proyecto resuelto.|  
|`ProjectReferences`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica las referencias del proyecto.|  
|`ResolvedOutputPaths`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la lista de rutas de acceso de referencia resueltas (y conserva los atributos de referencia de proyecto originales).|  
|`UnresolvedProjectReferences`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la lista de elementos de referencia de proyecto que no se pudieron resolver mediante la lista de resultados previamente resuelta.<br /><br /> Dado que Visual Studio solo resuelve previamente proyectos que no son de MSBuild, esto significa que las referencias de proyecto en esta lista están en el formato de MSBuild.|  
  
## <a name="remarks"></a>Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)