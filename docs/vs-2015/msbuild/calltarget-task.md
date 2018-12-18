---
title: Tarea CallTarget | Microsoft Docs
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
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc3c5822732a4ae584500bfe1c48d7ba9e29b038
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307682"
---
# <a name="calltarget-task"></a>CallTarget (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Invoca los destinos especificados en el archivo del proyecto.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
 En la siguiente tabla se describen los parámetros de la tarea `CallTarget`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`RunEachTargetSeparately`|Parámetro de salida `Boolean` opcional.<br /><br /> Si es `true`, se llama al motor de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] una vez por destino. Si es `false`, se llama al motor de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] una vez para compilar todos los destinos. El valor predeterminado es `false`.|  
|`TargetOutputs`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene las salidas de todos los destinos compilados.|  
|`Targets`|Parámetro `String[]` opcional.<br /><br /> Especifica los destinos que se compilarán.|  
|`UseResultsCache`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se devuelve el resultado almacenado en caché, si está presente.<br /><br /> **Nota** Cuando se ejecuta una tarea MSBuild, su salida se almacena en caché en un ámbito (ProjectFileName, GlobalProperties)[TargetNames] como una lista de elementos de compilación.|  
  
## <a name="remarks"></a>Comentarios  
 Si se produce un error en un destino especificado en `Targets` y `RunEachTargetSeparately` es `true`, la tarea sigue compilando los destinos restantes.  
  
 Si quiere compilar los destinos predeterminados, use la [tarea MSBuild](../msbuild/msbuild-task.md) y establezca el parámetro `Projects` igual a `$(MSBuildProjectFile)`.  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se llama a `TargetA` desde dentro de `CallOtherTargets`.  
  
```  
<Project DefaultTargets="CallOtherTargets"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <Target Name="CallOtherTargets">  
        <CallTarget Targets="TargetA"/>  
    </Target>  
  
    <Target Name="TargetA">  
        <Message Text="Building TargetA..." />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Destinos](../msbuild/msbuild-targets.md)



