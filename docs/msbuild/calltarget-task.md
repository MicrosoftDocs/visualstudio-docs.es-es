---
title: Tarea CallTarget | Microsoft Docs
description: Obtenga información sobre cómo usar la tarea CallTarget de MSBuild para invitar los destinos especificados dentro del archivo del proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3a2f124fa7e83e9f85e572276eed1851f42f7047
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939557"
---
# <a name="calltarget-task"></a>CallTarget (tarea)

Invoca los destinos especificados en el archivo del proyecto.

## <a name="task-parameters"></a>Parámetros de tareas

 En la siguiente tabla se describen los parámetros de la tarea `CallTarget` .

| Parámetro | Descripción |
|---------------------------| - |
| `RunEachTargetSeparately` | Parámetro de entrada `Boolean` opcional.<br /><br /> Si es `true`, se llama al motor de MSBuild una vez por destino. Si es `false`, se llama al motor de MSBuild una vez para compilar todos los destinos. El valor predeterminado es `false`. |
| `TargetOutputs` | Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene las salidas de todos los destinos compilados. |
| `Targets` | Parámetro `String[]` opcional.<br /><br /> Especifica los destinos que se compilarán. |
| `UseResultsCache` | Parámetro `Boolean` opcional.<br /><br /> Si es `true`, se devuelve el resultado almacenado en caché, si está presente.<br /><br /> **Nota** Cuando se ejecuta una tarea MSBuild, su salida se almacena en caché en un ámbito (ProjectFileName, GlobalProperties)[TargetNames] como una lista de elementos de compilación. |

## <a name="remarks"></a>Observaciones

 Si se produce un error en un destino especificado en `Targets` y `RunEachTargetSeparately` es `true`, la tarea sigue compilando los destinos restantes.

 Si quiere compilar los destinos predeterminados, use [MSBuild (Tarea)](../msbuild/msbuild-task.md) y establezca el parámetro `Projects` igual que `$(MSBuildProjectFile)`.

Cuando se usa `CallTarget`, MSBuild evalúa el destino al que se llama en un nuevo ámbito, en lugar de en el mismo ámbito desde el que se llama. Esto significa que los cambios en los elementos y propiedades en el destino al que se llama no son visibles para el destino desde el que se llama.  Para pasar información al destino desde el que se llama, use el parámetro de salida `TargetOutputs`.

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Ejemplo

 En el ejemplo siguiente se llama a `TargetA` desde dentro de `CallOtherTargets`.

```xml
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

- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Destinos](../msbuild/msbuild-targets.md)
