---
title: Tarea ResolveNonMSBuildProjectOutput | Microsoft Docs
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
- MSBuild, ResolveNonMSBuildProjectOutput task
- ResolveNonMSBuildProjectOutput task [MSBuild]
ms.assetid: a0b8fcec-8c8d-4867-85ac-5304c5108e5e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48a67d895c08d5966c2ea4b40140382db9157763
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575695"
---
# <a name="resolvenonmsbuildprojectoutput-task"></a>ResolveNonMSBuildProjectOutput (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ResolveNonMSBuildProjectOutput (tarea)](https://docs.microsoft.com/visualstudio/msbuild/resolvenonmsbuildprojectoutput-task).  
  
  
Determina los archivos de salida de las referencias de proyecto que no son de MSBuild.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `ResolveNonMSBuildProjectOutput` .  
  
|Parámetro|Descripción|  
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



