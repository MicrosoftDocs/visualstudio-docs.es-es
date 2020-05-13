---
title: Procedimiento Compilar de forma incremental | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4911bb131f5c5c878b82865b3dee61fd7bedbe1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634167"
---
# <a name="how-to-build-incrementally"></a>Procedimiento Compilación de forma incremental

Cuando se compila un proyecto grande, es importante que los componentes que se compilaron previamente y que aún están actualizados no se recompilen. Si todos los destinos se compilan cada vez, llevará más tiempo finalizar la compilación. Para habilitar las compilaciones incrementales (aquellas en las que solo se compilan los destinos no compilados con anterioridad o no actualizados), Microsoft Build Engine (MSBuild) compara las marcas de tiempo de los archivos de entrada con las de los archivos de salida y determina si debe omitir, compilar o recompilar parcialmente un destino. En cambio, debe haber una asignación unívoca entre las entradas y resultados. Se pueden usar las transformaciones para permitir que los destinos identifiquen esta asignación directa. Para obtener más información sobre transformaciones, vea [Transformaciones](../msbuild/msbuild-transforms.md).

## <a name="specify-inputs-and-outputs"></a>Definición de entradas y salidas

Es posible compilar un destino de forma incremental si se han especificado las entradas y los resultados en el archivo de proyecto.

#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Para especificar las entradas y los resultados de un destino

- Use los atributos `Inputs` y `Outputs` del elemento `Target`. Por ejemplo:

  ```xml
  <Target Name="Build"
      Inputs="@(CSFile)"
      Outputs="hello.exe">
  ```

MSBuild compara las marcas de tiempo de los archivos de entrada con las de los archivos de salida y determina si debe omitir, compilar o recompilar parcialmente un destino. En el ejemplo siguiente, si algún archivo de la lista de elementos `@(CSFile)` es más reciente que el archivo *hello.exe*, MSBuild ejecuta el destino; de lo contrario, se omite:

```xml
<Target Name="Build"
    Inputs="@(CSFile)"
    Outputs="hello.exe">

    <Csc
        Sources="@(CSFile)"
        OutputAssembly="hello.exe"/>
</Target>
```

Cuando las entradas y los resultados están especificados en un destino, puede suceder que cada resultado solo se asigne a una entrada o que no exista ninguna asignación directa entre resultados y entradas. Por ejemplo, en [Csc (Tarea)](../msbuild/csc-task.md) anterior, la salida *hello.exe* no se puede asignar a una única entrada porque depende de todas ellas.

> [!NOTE]
> Un destino en el que no exista asignación directa entre entradas y resultados se compilará con más frecuencia que un destino en el que cada resultado solo se puede asignar a una entrada. Esto se debe a que MSBuild no puede determinar qué resultados necesitan recompilarse si algunas de las entradas han cambiado.

Las tareas en las que se puede identificar una asignación directa entre salidas y entradas, como [LC (Tarea)](../msbuild/lc-task.md), son más adecuadas para las compilaciones incrementales que las tareas como [Csc](../msbuild/csc-task.md) y [Vbc](../msbuild/vbc-task.md), que producen un ensamblado de salida a partir de una serie de entradas.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa un proyecto que compila archivos de Ayuda para un sistema de Ayuda hipotético. El proyecto convierte archivos *.txt* de origen en archivos *.content* intermedios que, después, se combinan con archivos XML de metadatos para generar el archivo *.help* definitivo que usa el sistema de ayuda. El proyecto usa las tareas hipotéticas siguientes:

- `GenerateContentFiles`: Convierte archivos *.txt* en archivos *.content*.

- `BuildHelp`: Combina archivos *.content* y archivos XML de metadatos para compilar el archivo *.help* definitivo.

El proyecto usa transformaciones para crear una asignación unívoca entre las entradas y los resultados en la tarea `GenerateContentFiles`. Para obtener más información, consulte [Transformaciones](../msbuild/msbuild-transforms.md). Además, el elemento `Output` se establece para que use automáticamente los resultados de la tarea `GenerateContentFiles` como entradas para la tarea `BuildHelp`.

Este archivo de proyecto contiene los destinos `Convert` y `Build`. Las tareas `GenerateContentFiles` y `BuildHelp` se colocan respectivamente en los destinos `Convert` y `Build` para que se pueda compilar cada destino incrementalmente. Al usar el elemento `Output`, los resultados de la tarea `GenerateContentFiles` se colocan en la lista de elementos `ContentFile`, donde se pueden usar como entradas para la tarea `BuildHelp`. Si usa el elemento `Output` de esta manera, proporcionará automáticamente los resultados de una tarea como entradas para otra tarea y no será necesario enumerar manualmente cada elemento o las listas de elementos de cada tarea.

> [!NOTE]
> Aunque el destino de `GenerateContentFiles` se puede compilar incrementalmente, todas las salidas de ese destino se requieren siempre como entradas para el destino de `BuildHelp`. MSBuild proporciona automáticamente todas las salidas de un destino como entradas para otro destino cuando se usa el elemento `Output`.

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <TXTFile Include="*.txt"/>
        <XMLFiles Include="\metadata\*.xml"/>
    </ItemGroup>

    <Target Name = "Convert"
        Inputs="@(TXTFile)"
        Outputs="@(TXTFile->'%(Filename).content')">

        <GenerateContentFiles
            Sources = "@(TXTFile)">
            <Output TaskParameter = "OutputContentFiles"
                ItemName = "ContentFiles"/>
        </GenerateContentFiles>
    </Target>

    <Target Name = "Build" DependsOnTargets = "Convert"
        Inputs="@(ContentFiles);@(XMLFiles)"
        Outputs="$(MSBuildProjectName).help">

        <BuildHelp
            ContentFiles = "@(ContentFiles)"
            MetadataFiles = "@(XMLFiles)"
            OutputFileName = "$(MSBuildProjectName).help"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Vea también

- [Destinos](../msbuild/msbuild-targets.md)
- [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)
- [Transformaciones](../msbuild/msbuild-transforms.md)
- [Tarea Csc](../msbuild/csc-task.md)
- [Vbc (Tarea)](../msbuild/vbc-task.md)
