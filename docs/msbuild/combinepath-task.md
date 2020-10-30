---
title: CombinePath (Tarea) | Microsoft Docs
description: Obtenga información sobre cómo usar la tarea CombinePath de MSBuild para combinar las rutas de acceso especificadas en una única ruta de acceso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc33c3a413d788bd9a5a30a7db69c4c7766a3392
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796620"
---
# <a name="combinepath-task"></a>CombinePath (tarea)

Combina las rutas de acceso especificadas en una única ruta de acceso.
## <a name="task-parameters"></a>Parámetros de tareas

 En la siguiente tabla se describen los parámetros de [CombinePath (Tarea)](../msbuild/combinepath-task.md).


|Parámetro|Descripción|
|---------------|-----------------|
|`BasePath`|Parámetro `String` requerido.<br /><br /> Ruta de acceso base que se combinará con las demás rutas de acceso. Puede ser una ruta de acceso relativa, una ruta de acceso absoluta o estar en blanco.|
|`Paths`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Una lista de rutas de acceso individuales que se combinarán con el elemento BasePath para formar la ruta de acceso combinada. Las rutas acceso pueden ser relativas o absolutas.|
|`CombinedPaths`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> La ruta de acceso combinada que se crea mediante la tarea.|

## <a name="remarks"></a>Comentarios

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

 En el ejemplo siguiente se muestra cómo crear una estructura de carpetas de salida mediante `CombinePath` para construir la propiedad `$(OutputDirectory)` combinando una ruta de acceso raíz `$(PublishRoot)` concatenada con `$(ReleaseDirectory)` y una lista de subcarpetas `$(LangDirectories)`.

 ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <PublishRoot>C:\Site1\Release</PublishRoot>
  </PropertyGroup>

  <ItemGroup>
    <LangDirectories Include="en-us\;fr-fr\"/>
  </ItemGroup>

  <Target Name="CreateOutputDirectories" AfterTargets="Build">
    <CombinePath BasePath="$(PublishRoot)" Paths="@(LangDirectories)" >
      <Output TaskParameter="CombinedPaths" ItemName="OutputDirectories"/>
    </CombinePath>
    <MakeDir Directories="@(OutputDirectories)" />
  </Target>
```

La única propiedad que permite `CombinePath` que sea una lista es `Paths`, en cuyo caso la salida también es una lista. Por lo tanto, si `$(PublishRoot)` es *C:\Site1\\* y `$(ReleaseDirectory)` es *Release\\* , y `@(LangDirectories)` es *en-us\;fr-fr\\* , en este ejemplo se crean las carpetas:

- C:\Site1\Release\en-us\
- C:\Site1\Release\fr-fr\

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
