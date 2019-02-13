---
title: GetAssemblyIdentity (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GetAssemblyIdentity task
- GetAssemblyIdentity task [MSBuild]
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aadbc72f3d7bb21f313ddaae0de97ec45a7e72a3
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853773"
---
# <a name="getassemblyidentity-task"></a>GetAssemblyIdentity (tarea)
Recupera las identidades de ensamblado de los archivos especificados y genera la información de identidad.

## <a name="task-parameters"></a>Parámetros de tareas
En la siguiente tabla se describen los parámetros de la tarea `GetAssemblyIdentity` .

|Parámetro|Descripción|
|---------------|-----------------|
|`Assemblies`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene las identidades de ensamblado recuperadas.|
|`AssemblyFiles`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos de los que se recuperarán las identidades.|

## <a name="remarks"></a>Comentarios
Los elementos generados por el parámetro `Assemblies` contienen entradas de metadatos de elementos denominadas `Version`, `PublicKeyToken` y `Culture`.

Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se recupera la identidad de los archivos especificados en el elemento `MyAssemblies` y se generan en el elemento `MyAssemblyIdentities`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <MyAssemblies Include="File1.dll;File2.dll" />
    </ItemGroup>
    <Target Name="RetrieveIdentities">
        <GetAssemblyIdentity AssemblyFiles="@(MyAssemblies)">
            <Output TaskParameter="Assemblies" ItemName="MyAssemblyIdentities" />
        </GetAssemblyIdentity>
    </Target>
</Project>
```

## <a name="see-also"></a>Vea también
[Tareas](../msbuild/msbuild-tasks.md)  
[Referencia de tareas](../msbuild/msbuild-task-reference.md)
