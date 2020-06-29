---
title: Procesamiento por lotes de MSBuild | Microsoft Docs
ms.date: 06/09/2020
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d7c72d1da270220144cd5e6167ebecb66462ba9
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289279"
---
# <a name="msbuild-batching"></a>Procesamiento por lotes de MSBuild

MSBuild divide listas de elementos en distintas categorías, o lotes, según los metadatos de esos elementos y, luego, ejecuta un destino o una tarea una vez con cada lote.

## <a name="task-batching"></a>Procesamiento por lotes de tareas

El procesamiento por lotes de tareas le permite simplificar los archivos del proyecto porque proporciona una manera de dividir las listas de elementos en lotes diferentes y pasar cada uno de estos lotes a una tarea por separado. Esto significa que un archivo de proyecto solo necesita que la tarea y sus atributos se declaren una vez, aunque se puede ejecutar varias veces.

Para especificar que quiere que MSBuild realice el procesamiento por lotes en una tarea, debe usar la notación `%(ItemMetaDataName)` en uno de los atributos de la tarea. En el ejemplo siguiente, la lista de elementos `Example` se divide en lotes de acuerdo con el valor de los metadatos del elemento `Color` y pasa cada uno de los lotes a la tarea `MyTask` por separado.

> [!NOTE]
> Si no hace referencia a la lista de elementos en ninguna otra parte de los atributos de la tarea, o si el nombre de los metadatos puede ser ambiguo, puede usar la notación %(<ColecciónDeElementos.NombreMetadatosElemento>) para calificar totalmente el valor de los metadatos del elemento que se va a emplear para el procesamiento por lotes.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Para obtener ejemplos más específicos de procesamiento por lotes, vea [Metadatos de elementos en el procesamiento por lotes de tareas](../msbuild/item-metadata-in-task-batching.md).

## <a name="target-batching"></a>Procesamiento por lotes de destinos

MSBuild comprueba si las entradas y las salidas de un destino están actualizadas antes de ejecutar el destino. Si las entradas y salidas están actualizadas, el destino se omite. Si una tarea dentro de un destino usa el procesamiento por lotes, MSBuild debe determinar si las entradas y las salidas de cada lote de elementos están actualizadas. En caso contrario, el destino se ejecuta cada vez que se le llama.

En el ejemplo siguiente se muestra un elemento `Target` que contiene un atributo `Outputs` con la notación `%(ItemMetadataName)`. MSBuild dividirá la lista de elementos `Example` en lotes de acuerdo con los metadatos del elemento `Color` y analizará las marcas de tiempo de los archivos de salida para cada lote. Si las salidas de un lote no están actualizadas, se ejecuta el destino. En caso contrario, se omite el destino.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Example Include="Item1">
            <Color>Blue</Color>
        </Example>
        <Example Include="Item2">
            <Color>Red</Color>
        </Example>
    </ItemGroup>

    <Target Name="RunMyTask"
        Inputs="@(Example)"
        Outputs="%(Color)\MyFile.txt">
        <MyTask
            Sources = "@(Example)"
            Output = "%(Color)\MyFile.txt"/>
    </Target>

</Project>
```

Para obtener otro ejemplo de procesamiento por lotes de destinos, vea [Metadatos de elementos en el procesamiento por lotes de destinos](../msbuild/item-metadata-in-target-batching.md).

## <a name="item-and-property-mutations"></a>Mutaciones de elemento y propiedad

En esta sección se describe cómo entender los efectos de cambiar las propiedades y los metadatos de elemento cuando se usa el procesamiento por lotes de destino o el procesamiento por lotes de tareas.

Como el procesamiento por lotes de destino y el procesamiento por lotes de tareas son dos operaciones de MSBuild distintas, es importante entender exactamente qué forma de procesamiento por lotes MSBuild usa en cada caso. Cuando la sintaxis de procesamiento por lotes `%(ItemMetadataName)` aparece en una tarea en un destino, pero no en un atributo en el destino, MSBuild usa el procesamiento por lotes de tareas. La única manera de especificar el procesamiento por lotes de destino es usar la sintaxis de procesamiento por lotes en un atributo de destino, habitualmente el atributo `Outputs`.

Con el procesamiento por lotes de destino y el procesamiento por lotes de tareas, se puede considerar que los lotes se ejecutan de forma independiente. Todos los lotes comienzan con una copia del mismo estado inicial de los valores de metadatos de elemento y de propiedad. Cualquier mutación de los valores de propiedad durante la ejecución por lotes no es visible para otros lotes. Considere el ejemplo siguiente:

```xml
  <ItemGroup>
    <Thing Include="2" Color="blue" />
    <Thing Include="1" Color="red" />
  </ItemGroup>

  <Target Name="DemoIndependentBatches">
    <ItemGroup>
      <Thing Condition=" '%(Color)' == 'blue' ">
        <Color>red</Color>
        <NeededColorChange>true</NeededColorChange>
      </Thing>
    </ItemGroup>
    <Message Importance="high"
             Text="Things: @(Thing->'%(Identity) is %(Color); needed change=%(NeededColorChange)')"/>
  </Target>
```

El resultado es el siguiente:

```output
Target DemoIndependentBatches:
  Things: 2 is red; needed change=true;1 is red; needed change=
```

El elemento `ItemGroup` en el destino es implícitamente una tarea y con `%(Color)` en el atributo `Condition`, se realiza el procesamiento por lotes de tareas. Hay dos lotes: uno para rojo y otro para azul. La propiedad `%(NeededColorChange)` solo se establece si los metadatos `%(Color)` son azul y el valor solo afecta al elemento individual que coincidió con la condición cuando se ejecutó el lote azul. El atributo `Text` de la tarea `Message` no desencadena el procesamiento por lotes, a pesar de la sintaxis `%(ItemMetadataName)`, porque se usa dentro de una transformación de elemento.

Los lotes se ejecutan de forma independiente, pero no en paralelo. Esto marca una diferencia cuando se accede a los valores de metadatos que cambian en la ejecución por lotes. En el caso de que se establezca una propiedad basada en algunos metadatos de la ejecución por lotes, la propiedad tomaría el *último* valor establecido:

```xml
   <PropertyGroup>
       <SomeProperty>%(SomeItem.MetadataValue)</SomeProperty>
   </PropertyGroup>
```

Después de la ejecución del lote, la propiedad conserva el valor final de `%(MetadataValue)`.

Aunque los lotes se ejecutan de forma independiente, es importante tener en cuenta la diferencia entre el procesamiento por lotes de destino y el procesamiento por lotes de tareas y saber qué tipo se aplica a su situación. Considere el ejemplo para entender mejor la importancia de esta distinción.

Las tareas pueden ser implícitas en lugar de explícitas, lo que puede ser confuso cuando el procesamiento por lotes de tareas se produce con tareas implícitas. Cuando aparece un elemento `PropertyGroup` o `ItemGroup` en un `Target`, cada declaración de propiedad del grupo se trata implícitamente como una tarea [CreateProperty](createproperty-task.md) o [CreateItem](createitem-task.md) independiente. Esto significa que el comportamiento es diferente cuando el destino se procesa por lotes en comparación con cuando no es así (es decir, cuando carece de la sintaxis `%(ItemMetadataName)` en el atributo `Outputs`). Cuando el destino se procesa por lotes, el `ItemGroup` se ejecuta una vez por cada destino, pero cuando no se procesa por lotes, los equivalentes implícitos de las tareas `CreateItem` o `CreateProperty` se procesan por lotes mediante el procesamiento por lotes de tareas, por lo que el destino solo se ejecuta una vez y cada elemento o propiedad del grupo se procesa por lotes de manera independiente mediante el procesamiento por lotes de tareas.

En el ejemplo siguiente se muestra el procesamiento por lotes de destino en comparación con el procesamiento por lotes de tareas en el caso de que hayan mutado los metadatos. Considere una situación en la que tiene las carpetas A y B con algunos archivos:

```
A\1.stub
B\2.stub
B\3.stub
```

Ahora fíjese en la salida de estos dos proyectos similares.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build" Outputs="%(StubDirs.Identity)">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

El resultado es el siguiente:

```output
Test1:
  >> A\ 'A\' 'A'
Test1:
  >> B\ 'B\' 'B'
```

Ahora, quite el atributo `Outputs` que especificó el procesamiento por lotes de destino.

```xml
    <ItemGroup>
      <StubFiles Include="$(MSBuildThisFileDirectory)**\*.stub"/>

      <StubDirs Include="@(StubFiles->'%(RecursiveDir)')"/>
    </ItemGroup>

    <Target Name="Test1" AfterTargets="Build">
      <PropertyGroup>
        <ComponentDir>%(StubDirs.Identity)</ComponentDir>
        <ComponentName>$(ComponentDir.TrimEnd('\'))</ComponentName>
      </PropertyGroup>

      <Message Text=">> %(StubDirs.Identity) '$(ComponentDir)' '$(ComponentName)'"/>
    </Target>
```

El resultado es el siguiente:

```output
Test1:
  >> A\ 'B\' 'B'
  >> B\ 'B\' 'B'
```

Observe que el encabezado `Test1` solo se imprime una vez, pero en el ejemplo anterior, se imprimió dos veces. Esto significa que el destino no se procesa por lotes.  Y, como resultado, la salida es confusamente diferente.

La razón es que, cuando se usa el procesamiento por lotes de destino, cada lote de destino ejecuta todo en el destino con su propia copia independiente de todas las propiedades y elementos, pero cuando se omite el atributo `Outputs`, las líneas individuales del grupo de propiedades se tratan como tareas distintas y potencialmente procesadas por lotes. En este caso, la tarea `ComponentDir` se procesa por lotes (usa la sintaxis `%(ItemMetadataName)`), de modo que, en el momento en que se ejecuta la línea `ComponentName`, se han completado los dos lotes de la línea `ComponentDir` y la segunda que se ejecutó determinó el valor, tal como se muestra en la segunda línea.

## <a name="property-functions-using-metadata"></a>Funciones de propiedad con metadatos

El procesamiento por lotes puede controlarse mediante funciones de propiedad que incluyen metadatos. Por ejemplo,

`$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`

utiliza <xref:System.IO.Path.Combine%2A> para combinar una ruta de acceso de directorio raíz con una ruta de acceso de elemento de compilación.

Es posible que las funciones de propiedad no aparezcan en los valores de los metadatos. Por ejemplo,

`%(Compile.FullPath.Substring(0,3))`

no se permite.

Para obtener más información sobre las funciones de propiedad, vea [Funciones de propiedad](../msbuild/property-functions.md).

## <a name="see-also"></a>Vea también

- [Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)
- [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)
