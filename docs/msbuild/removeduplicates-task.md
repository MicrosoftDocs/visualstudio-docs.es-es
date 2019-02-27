---
title: RemoveDuplicates (Tarea) | Microsoft Docs
ms.date: 03/01/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 027e1f4894660b0198ed8a6df862e66e41cde409
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56642929"
---
# <a name="removeduplicates-task"></a>RemoveDuplicates (tarea)
Quita los elementos duplicados de la colección de elementos especificada.

## <a name="parameters"></a>Parámetros
 En la siguiente tabla se describen los parámetros de la tarea `RemoveDuplicates` .

|Parámetro|Descripción|
|---------------|-----------------|
|`Filtered`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene una colección de elementos sin elementos duplicados. Se conserva el orden de los elementos de entrada, manteniendo la primera instancia de cada elemento duplicado.|
|`Inputs`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Colección de elementos de la que se van a quitar los elementos duplicados.|

## <a name="remarks"></a>Comentarios
 Esta tarea no distingue mayúsculas de minúsculas y no compara los metadatos de los elementos al determinar los duplicados.

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se usa la tarea `RemoveDuplicates` para quitar los elementos duplicados de la colección de elementos `MyItems`. Cuando la tarea ha finalizado, la colección de elementos `FilteredItems` contiene un elemento.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile.cs"/>
        <MyItems Include="MyFile.cs">
            <Culture>fr</Culture>
        </MyItems>
        <MyItems Include="myfile.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

 En el ejemplo siguiente se muestra que la tarea `RemoveDuplicates` conserva su orden de entrada. Cuando la tarea está completa, la colección de elementos `FilteredItems` contiene los elementos *MyFile2.cs*, *MyFile1.cs* y *MyFile3.cs*, en ese orden.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile2.cs"/>
        <MyItems Include="MyFile1.cs" />
        <MyItems Include="MyFile3.cs" />
        <MyItems Include="myfile1.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

## <a name="see-also"></a>Vea también
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
- [Tareas](../msbuild/msbuild-tasks.md)
