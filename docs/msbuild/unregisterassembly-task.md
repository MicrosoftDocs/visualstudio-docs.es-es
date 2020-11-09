---
title: UnregisterAssembly (Tarea) | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea UnregisterAssembly para anular el registro de los ensamblados especificados con fines de interoperabilidad COM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UnregisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UnregisterAssembly task
- UnregisterAssembly task [MSBuild]
ms.assetid: 04f549dd-3591-4dda-9c3a-cf6ede9df2c3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 068073b2d84d95ad3d86abe582691be0dd4af895
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046922"
---
# <a name="unregisterassembly-task"></a>UnregisterAssembly (tarea)

Elimina del Registro los ensamblados especificados para la interoperabilidad COM. Invierte la [tarea RegisterAssembly](../msbuild/registerassembly-task.md).

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `UnregisterAssembly` .

|Parámetro|Description|
|---------------|-----------------|
|`Assemblies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los ensamblados que se eliminarán del Registro.|
|`AssemblyListFile`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Contiene información sobre el estado entre las tareas `RegisterAssembly` y `UnregisterAssembly`. Impide que la tarea intente eliminar del Registro un ensamblado que no se pudo registrar en la tarea `RegisterAssembly`.<br /><br /> Si se especifica este parámetro, se omiten los parámetros `Assemblies` y `TypeLibFiles`.|
|`TypeLibFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Elimina del Registro la biblioteca de tipos especificada del ensamblado especificado. **Nota** : Este parámetro solo es necesario si el nombre de archivo de la biblioteca de tipos es diferente del nombre del ensamblado.|

## <a name="remarks"></a>Comentarios

 No es necesario disponer de un ensamblado para que esta tarea se realice correctamente. Si intenta eliminar del Registro un ensamblado que no existe, la tarea se realizará correctamente y se mostrará una advertencia. Esto se debe a que esta tarea se encarga de quitar el registro del ensamblado del Registro. Si el ensamblado no existe, no se encontrará en el Registro, por lo que la tarea ha conseguido su propósito.

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.AppDomainIsolatedTaskExtension>, que a su vez hereda de la clase <xref:System.MarshalByRefObject>. La clase `MarshalByRefObject` proporciona la misma funcionalidad que la clase <xref:Microsoft.Build.Utilities.Task>, pero se pueden crear instancias de esta clase en su propio dominio de aplicación.

## <a name="example"></a>Ejemplo

 En el ejemplo siguiente se utiliza la tarea `UnregisterAssembly` para eliminar del Registro el ensamblado en la ruta de acceso especificada por las propiedades `OutputPath` y `FileName`, si existe.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <OutputPath>\Output\</OutputPath>
        <FileName>MyFile.dll</FileName>
    </PropertyGroup>
    <Target Name="UnregisterAssemblies">
        <UnregisterAssembly
            Condition="Exists('$(OutputPath)$(FileName)')"
            Assemblies="$(OutputPath)$(FileName)" />
    </Target>

</Project>
```

## <a name="see-also"></a>Consulte también

- [RegisterAssembly (tarea)](../msbuild/registerassembly-task.md)
- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)