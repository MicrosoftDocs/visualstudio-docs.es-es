---
title: Tarea CreateProperty | Microsoft Docs
description: Use la tarea CreateProperty de MSBuild para rellenar las propiedades con los valores que se pasaron, lo que permite que los valores se copien de una propiedad o cadena a otra.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d7dd8d7f5a50998832a8fac6f47bf66e9a6bbe9
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796192"
---
# <a name="createproperty-task"></a>CreateProperty (tarea)

Rellena las propiedades con los valores pasados. Esto permite que los valores se copien de una propiedad o cadena a otra.

## <a name="attributes"></a>Atributos

En la siguiente tabla se describen los parámetros de la tarea `CreateProperty` .

| Parámetro | Descripción |
|------------------| - |
| `Value` | Parámetro de salida `String` opcional.<br /><br /> Especifica el valor que se copiará en la nueva propiedad. |
| `ValueSetByTask` | Parámetro de salida `String` opcional.<br /><br /> Contiene el mismo valor que el parámetro `Value`. Use este parámetro únicamente cuando quiera impedir que MSBuild establezca la propiedad de salida cuando omita el destino que lo contiene porque las salidas están actualizadas. |

## <a name="remarks"></a>Comentarios

Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa la tarea `CreateProperty` para crear la propiedad `NewFile` mediante la combinación de los valores de la propiedad `SourceFilename` y `SourceFileExtension`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <SourceFilename>Module1</SourceFilename>
        <SourceFileExtension>vb</SourceFileExtension>
    </PropertyGroup>

    <Target Name="CreateProperties">

        <CreateProperty
            Value="$(SourceFilename).$(SourceFileExtension)">
            <Output
                TaskParameter="Value"
                PropertyName="NewFile" />
        </CreateProperty>

    </Target>

</Project>
```

Después de ejecutar el proyecto, el valor de la propiedad `NewFile` es *Module1.vb* .

## <a name="see-also"></a>Vea también

- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Tareas](../msbuild/msbuild-tasks.md)
