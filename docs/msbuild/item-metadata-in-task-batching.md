---
title: Metadatos de elementos en el procesamiento por lotes de tareas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6152b0e64286c3cadedfcafb0ac530616c4012a6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288993"
---
# <a name="item-metadata-in-task-batching"></a>Metadatos de elementos en el procesamiento por lotes de tareas

MSBuild es capaz de dividir listas de elementos en distintas categorías, o lotes, según los metadatos de esos elementos y, luego, ejecutar una tarea una vez con cada lote. Puede resultar complicado entender exactamente qué elementos se pasan con cada lote. En este tema se tratan los escenarios comunes siguientes en los que se utiliza el procesamiento por lotes.

- Dividir una lista de elementos en lotes

- Dividir varias listas de elementos en lotes

- Procesar por lotes un elemento cada vez

- Filtrar listas de elementos

Para obtener más información sobre el procesamiento por lotes con MSBuild, vea [Procesamiento por lotes](../msbuild/msbuild-batching.md).

## <a name="divide-an-item-list-into-batches"></a>Dividir una lista de elementos en lotes

El procesamiento por lotes permite dividir una lista de elementos en distintos lotes basándose en los metadatos de esos elementos, y luego pasar cada uno de los lotes a una tarea por separado. Esto resulta útil para compilar ensamblados satélite.

En el ejemplo siguiente, se muestra cómo dividir una lista de elementos en lotes basándose en los metadatos de los elementos. La lista de elementos `ExampColl` se divide en tres lotes según los metadatos del elemento `Number`. La presencia de `%(ExampColl.Number)` en el atributo `Text` indica a MSBuild que se debe realizar un procesamiento por lotes. La lista de elementos `ExampColl` se divide en tres lotes según los metadatos de `Number` y cada lote se pasa a la tarea por separado.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>
    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

[Message (Tarea)](../msbuild/message-task.md) muestra la información siguiente:

`Number: 1 -- Items in ExampColl: Item1;Item4`

`Number: 2 -- Items in ExampColl: Item2;Item5`

`Number: 3 -- Items in ExampColl: Item3;Item6`

## <a name="divide-several-item-lists-into-batches"></a>Dividir varias listas de elementos en lotes

MSBuild puede dividir varias listas de elementos en lotes basándose en los mismos metadatos. Esto facilita la división de diferentes listas de elementos en lotes para compilar varios ensamblados. Por ejemplo, se puede dividir una lista de elementos de archivos *.cs* en un lote de aplicación y un lote de ensamblado, y dividir una lista de elementos de archivos de recursos en un lote de aplicación y un lote de ensamblado. A continuación, se puede utilizar el procesamiento por lotes para pasar estas listas de elementos a una misma tarea y compilar la aplicación y el ensamblado.

> [!NOTE]
> Si una lista de elementos pasada a una tarea no contiene ningún elemento con los metadatos a los que se hace referencia, todos los elementos de esa lista se pasan a todos los lotes.

En el ejemplo siguiente, se muestra cómo dividir varias listas de elementos en lotes según los metadatos de los elementos. Las listas de elementos `ExampColl` y `ExampColl2` se han dividido en tres lotes cada una, basándose en los metadatos del elemento `Number`. La presencia de `%(Number)` en el atributo `Text` indica a MSBuild que se debe realizar un procesamiento por lotes. Las listas de elementos `ExampColl` y `ExampColl2` se dividen en tres lotes según los metadatos de `Number` y cada lote se pasa a la tarea por separado.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>

        <ExampColl2 Include="Item4">
            <Number>1</Number>
        </ExampColl2>
        <ExampColl2 Include="Item5">
            <Number>2</Number>
        </ExampColl2>
        <ExampColl2 Include="Item6">
            <Number>3</Number>
        </ExampColl2>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>
    </Target>

</Project>
```

[Message (Tarea)](../msbuild/message-task.md) muestra la información siguiente:

`Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`

`Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`

`Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`

## <a name="batch-one-item-at-a-time"></a>Procesamiento por lotes de un elemento cada vez

El procesamiento por lotes también se puede realizar en metadatos de elementos conocidos que se asignan a cada elemento durante su creación. De este modo se garantiza que cada elemento de una colección disponga de metadatos que utilizar para el procesamiento por lotes. El valor de metadatos `Identity` es único para cada elemento y resulta de gran utilidad para dividir cada elemento de una lista de elementos en un lote independiente. Para obtener una lista completa de metadatos de elementos conocidos, vea [Metadatos de los elementos conocidos](../msbuild/msbuild-well-known-item-metadata.md).

En el ejemplo siguiente se muestra cómo procesar por lotes cada uno de los elementos de una lista, de uno en uno. Dado que el valor de metadatos `Identity` de cada elemento es único, la lista de elementos `ExampColl` se divide en seis lotes, cada uno de los cuales contiene un elemento de la lista. La presencia de `%(Identity)` en el atributo `Text` indica a MSBuild que se debe realizar un procesamiento por lotes.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1"/>
        <ExampColl Include="Item2"/>
        <ExampColl Include="Item3"/>
        <ExampColl Include="Item4"/>
        <ExampColl Include="Item5"/>
        <ExampColl Include="Item6"/>

    </ItemGroup>

    <Target Name="ShowMessage">
        <Message
            Text = "Identity: '%(Identity)' -- Items in ExampColl: @(ExampColl)"/>
    </Target>

</Project>
```

[Message (Tarea)](../msbuild/message-task.md) muestra la información siguiente:

```output
Identity: 'Item1' -- Items in ExampColl: Item1
Identity: 'Item2' -- Items in ExampColl: Item2
Identity: 'Item3' -- Items in ExampColl: Item3
Identity: 'Item4' -- Items in ExampColl: Item4
Identity: 'Item5' -- Items in ExampColl: Item5
Identity: 'Item6' -- Items in ExampColl: Item6
```

## <a name="filter-item-lists"></a>Filtro de elementos en listas

El procesamiento por lotes se puede utilizar para filtrar y extraer determinados elementos de una lista de elementos antes de pasarla a una tarea. Por ejemplo, si se aplica como filtro el valor de metadatos de elementos conocidos `Extension`, se puede ejecutar una tarea únicamente en los archivos que tienen una extensión concreta.

El ejemplo siguiente muestra cómo dividir una lista de elementos en lotes basándose en los metadatos de los elementos y, a continuación, filtrar los lotes al pasarlos a una tarea. La lista de elementos `ExampColl` se divide en tres lotes según los metadatos del elemento `Number`. El atributo `Condition` de la tarea especifica que solo se pasarán a la tarea los lotes cuyo valor de metadatos del elemento `Number` sea `2`.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>

        <ExampColl Include="Item1">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item2">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item3">
            <Number>3</Number>
        </ExampColl>
        <ExampColl Include="Item4">
            <Number>1</Number>
        </ExampColl>
        <ExampColl Include="Item5">
            <Number>2</Number>
        </ExampColl>
        <ExampColl Include="Item6">
            <Number>3</Number>
        </ExampColl>

    </ItemGroup>

    <Target Name="Exec">
        <Message
            Text = "Items in ExampColl: @(ExampColl)"
            Condition="'%(Number)'=='2'"/>
    </Target>

</Project>
```

[Message (Tarea)](../msbuild/message-task.md) muestra la información siguiente:

```
Items in ExampColl: Item2;Item5
```

## <a name="see-also"></a>Vea también

- [Metadatos de los elementos conocidos](../msbuild/msbuild-well-known-item-metadata.md)
- [Elemento Item (MSBuild)](../msbuild/item-element-msbuild.md)
- [Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Procesamiento por lotes](../msbuild/msbuild-batching.md)
- [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
