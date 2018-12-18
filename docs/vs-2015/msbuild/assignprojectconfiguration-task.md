---
title: AssignProjectConfiguration (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.assetid: 09633a0b-8f6f-4aba-8058-7cb4d13ce2c0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57e513dc8b5cb914fd26f23b63e1a7e7d4908b76
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49290516"
---
# <a name="assignprojectconfiguration-task"></a>AssignProjectConfiguration (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Esta tarea acepta cadenas de configuración de lista y las asigna a los proyectos especificados.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la tarea `AssignProjectConfiguration`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`SolutionConfigurationContents`|Parámetro de salida `string` opcional.<br /><br /> Contiene una cadena XML que incluye una configuración de proyecto para cada proyecto. Las configuraciones se asignan a los proyectos con nombre.|  
|`DefaultToVcxPlatformMapping`|Parámetro de salida `string` opcional.<br /><br /> Contiene una lista delimitada por puntos y coma de asignaciones de los nombres de plataforma que utilizan<br /><br /> la mayoría de los tipos a los que usan los archivos .vcxproj.<br /><br /> Por ejemplo:<br /><br /> `"AnyCPU=Win32;X86=Win32;X64=X64"`|  
|`VcxToDefaultPlatformMapping`|Optional<br /><br /> Parámetro de salida `string`.<br /><br /> Contiene una lista delimitada por puntos y coma de asignaciones de los nombres de plataforma de .vcxproj a los nombres de plataforma usados por la mayoría de los tipos.<br /><br /> Por ejemplo:<br /><br /> `"Win32=AnyCPU;X64=X64"`|  
|`CurrentProjectConfiguration`|Parámetro de salida `string` opcional.<br /><br /> Contiene la configuración del proyecto actual.|  
|`CurrentProjectPlatform`|Parámetro de salida `string` opcional.<br /><br /> Contiene la plataforma del proyecto actual.|  
|`OnlyReferenceAndBuildProjectsEnabledInSolutionConfiguration`|Parámetro de salida `bool` opcional.<br /><br /> Contiene una marca que indica que se deben compilar las referencias incluso si se han deshabilitado en la configuración del proyecto.|  
|`ShouldUnsetParentConfigurationAndPlatform`|Parámetro de salida `bool` opcional.<br /><br /> Contiene una marca que especifica si deben anular la configuración primaria y la plataforma.|  
|`OutputType`|Parámetro de salida `string` opcional.<br /><br /> Contiene el tipo de salida del proyecto.|  
|`ResolveConfigurationPlatformUsingMappings`|Parámetro de salida `bool` opcional.<br /><br /> Contiene una marca que indica si la compilación debe utilizar las asignaciones predeterminadas para resolver la configuración y la plataforma de las referencias del proyecto pasadas.|  
|`AssignedProjects`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la lista de rutas de acceso de referencia resueltas.|  
|`UnassignedProjects`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la lista de elementos de referencia de proyecto que no se pudieron resolver mediante la lista de resultados previamente resuelta.|  
  
## <a name="remarks"></a>Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



