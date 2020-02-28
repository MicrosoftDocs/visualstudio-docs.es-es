---
title: Delete (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69f6be4c80519b023d3f11c28f3d5f5b2bf8f8e1
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557958"
---
# <a name="delete-task"></a>Delete (tarea)
Elimina los archivos especificados.

## <a name="parameters"></a>Parámetros
En la siguiente tabla se describen los parámetros de la tarea `Delete` .

|Parámetro|Descripción|
|---------------|-----------------|
|`DeletedFiles`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los archivos que se eliminaron correctamente.|
|`Files`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos que se van a eliminar.|
|`TreatErrorsAsWarnings`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, los errores se registran como advertencias. El valor predeterminado es `false`.|

## <a name="remarks"></a>Comentarios
Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Tenga cuidado al usar comodines con la tarea `Delete`. Puede eliminar fácilmente los archivos equivocados con expresiones como `$(SomeProperty)\**\*.*` o `$(SomeProperty)/**/*.*`, especialmente si la propiedad se evalúa como una cadena vacía, en cuyo caso el parámetro `Files` puede evaluarse como raíz de la unidad y eliminar mucho más de lo que se quiere.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se elimina el archivo *MyApp.pdb*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <AppName>MyApp</AppName>
    </PropertyGroup>

    <Target Name="DeleteFiles">
        <Delete Files="$(AppName).pdb" />
    </Target>
</Project>
```

## <a name="see-also"></a>Vea también
- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
