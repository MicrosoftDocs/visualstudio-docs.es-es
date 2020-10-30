---
title: Tarea AssignTargetPath| Microsoft Docs
description: Use la tarea AssignTargetPath de MSBuild para aceptar una lista de archivos y agregar atributos TargetPath si todavía no se especifican.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e56bb8817551e24d1b5aceef2f571e35f1db43e
ms.sourcegitcommit: d3bca34f82de03fa34ecdd72233676c17fb3cb14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92353335"
---
# <a name="assigntargetpath-task"></a>Tarea AssignTargetPath

Esta tarea acepta una lista de archivos y agrega atributos `<TargetPath>` si aún no se han especificado.

## <a name="task-parameters"></a>Parámetros de tareas

En la siguiente tabla se describen los parámetros de la tarea `AssignTargetPath` .

|Parámetro|Descripción|
|---------------|-----------------|
|`RootFolder`|Parámetro de entrada `string` opcional.<br /><br /> Contiene la ruta de acceso a la carpeta que contiene los vínculos de destino.|
|`Files`|Parámetro de entrada <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene la lista de entrada de archivos.|
|`AssignedFiles`|Opcional<br /><br /> Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> `[]`.<br /><br /> Contiene la lista de archivos resultante.|

## <a name="remarks"></a>Comentarios

Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se ejecuta la tarea `AssignTargetPath` para configurar un proyecto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyProject">
        <AssignTargetPath
RootFolder="Resources"
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
        </AssignTargetPath>
    </Target>
</Project>
```

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
