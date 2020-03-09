---
title: Elemento Target (MSBuild) | Microsoft Docs
ms.date: 06/13/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Target
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Target element [MSBuild]
- <Target> element [MSBuild]
ms.assetid: 350f6fc2-86b3-45f2-a31e-ece0e6bd4dca
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79686132adce043b4864d545f0912564709cfe2c
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631983"
---
# <a name="target-element-msbuild"></a>Elemento Target (MSBuild)

Contiene un conjunto de tareas para que MSBuild las ejecute de manera secuencial.

 \<Project> \<Target>

## <a name="syntax"></a>Sintaxis

```xml
<Target Name="Target Name"
        Inputs="Inputs"
        Outputs="Outputs"
        Returns="Returns"
        KeepDuplicateOutputs="true/false"
        BeforeTargets="Targets"
        AfterTargets="Targets"
        DependsOnTargets="DependentTarget"
        Condition="'String A' == 'String B'"
        Label="Label">
    <Task>... </Task>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <OnError... />
</Target>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Name`|Atributo necesario.<br /><br /> Nombre del destino.|
|`Condition`|Atributo opcional.<br /><br /> La condición que se va a evaluar. Si la condición se evalúa como `false`, el destino no ejecutará el cuerpo del destino ni los destinos que se establecen en el atributo `DependsOnTargets`. Para obtener más información sobre las condiciones, consulte [Condiciones](../msbuild/msbuild-conditions.md).|
|`Inputs`|Atributo opcional.<br /><br /> Los archivos que forman entradas en este destino. Si hay varios archivos, se separan con punto y coma. Las marcas de tiempo de los archivos se compararán con las marcas de tiempo de los archivos en `Outputs` para determinar si `Target` está actualizado. Para obtener más información, vea [Compilaciones incrementales](../msbuild/incremental-builds.md), [Cómo: Compilar de forma incremental](../msbuild/how-to-build-incrementally.md) y [Transformaciones](../msbuild/msbuild-transforms.md).|
|`Outputs`|Atributo opcional.<br /><br /> Los archivos que forman salidas en este destino. Si hay varios archivos, se separan con punto y coma. Las marcas de tiempo de los archivos se compararán con las marcas de tiempo de los archivos en `Inputs` para determinar si `Target` está actualizado. Para obtener más información, vea [Compilaciones incrementales](../msbuild/incremental-builds.md), [Cómo: Compilar de forma incremental](../msbuild/how-to-build-incrementally.md) y [Transformaciones](../msbuild/msbuild-transforms.md).|
|`Returns`|Atributo opcional.<br /><br /> El conjunto de elementos que estará disponible para las tareas que llaman a este destino, por ejemplo, las tareas de MSBuild. Si hay varios destinos, se separan con punto y coma. Si los destinos en el archivo no tienen atributos `Returns`, los atributos Outputs se utilizan en su lugar para este propósito.|
|`KeepDuplicateOutputs`|Atributo Boolean opcional.<br /><br /> Si `true`, se registran varias referencias al mismo elemento en las devoluciones del destino.  De manera predeterminada, este atributo es `false`.|
|`BeforeTargets`|Atributo opcional.<br /><br /> Una lista separada por punto y coma de nombres de destino.  Cuando se especifica, indica que este destino se debe ejecutar antes que los destinos especificados. Esto permite que el autor del proyecto amplíe un conjunto de destinos existentes sin tener que modificarlos directamente. Para más información, consulte [Orden de compilación de destinos](../msbuild/target-build-order.md).|
|`AfterTargets`|Atributo opcional.<br /><br /> Una lista separada por punto y coma de nombres de destino. Cuando se especifica, indica que este destino se debe ejecutar después de los destinos especificados. Esto permite que el autor del proyecto amplíe un conjunto de destinos existentes sin tener que modificarlos directamente. Para más información, consulte [Orden de compilación de destinos](../msbuild/target-build-order.md).|
|`DependsOnTargets`|Atributo opcional.<br /><br /> Se pueden ejecutar los destinos que se deben ejecutar antes que este destino, o se puede realizar un análisis de dependencias de nivel superior. Si hay varios destinos, se separan con punto y coma.|
|`Label`|Atributo opcional.<br /><br /> Un identificador que puede identificar u ordenar elementos de usuario y del sistema.|

### <a name="child-elements"></a>Elementos secundarios

| Elemento | Descripción |
| - | - |
| [Task](../msbuild/task-element-msbuild.md) | Crea y ejecuta una instancia de una tarea de MSBuild. Puede haber cero o más tareas en un destino. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Contiene un conjunto de elementos `Property` definidos por el usuario. A partir de .NET Framework 3.5, un elemento `Target` puede contener elementos `PropertyGroup`. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Contiene un conjunto de elementos `Item` definidos por el usuario. A partir de .NET Framework 3.5, un elemento `Target` puede contener elementos `ItemGroup`. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md). |
| [OnError](../msbuild/onerror-element-msbuild.md) | Hace que uno o varios destinos se ejecuten si el atributo `ContinueOnError` es ErrorAndStop (o `false`) para una tarea con error. Puede haber cero o más elementos `OnError` en un destino. Si hay elementos `OnError` presentes, deben ser los últimos elementos en el elemento `Target`.<br /><br /> Para información sobre el atributo `ContinueOnError`, consulte [Elemento Task (MSBuild)](../msbuild/task-element-msbuild.md). |

### <a name="parent-elements"></a>Elementos primarios

| Elemento | Descripción |
| - | - |
| [Proyecto](../msbuild/project-element-msbuild.md) | Elemento raíz necesario de un archivo de proyecto de MSBuild. |

## <a name="remarks"></a>Comentarios

 El primer destino que se ejecutará se especifica en tiempo de ejecución. Los destinos pueden tener dependencias en otros destinos. Por ejemplo, un destino para la implementación depende de un destino para la compilación. El motor de MSBuild ejecuta las dependencias en el orden en que aparecen en el atributo `DependsOnTargets`, de izquierda a derecha. Para obtener más información, consulte [Destinos](../msbuild/msbuild-targets.md).

 MSBuild depende del orden de importación y la última definición de un destino con un atributo `Name` específico es la definición usada.

 Un destino solo se ejecuta una vez durante una compilación, incluso si más de un destino depende de él.

 Si se omite un destino porque el atributo `Condition` se evalúa como `false`, todavía se puede ejecutar si se invoca más adelante durante la compilación y el atributo `Condition` se evalúa como `true` en ese momento.

 Antes de MSBuild 4, `Target` devolvía todos los elementos que se especificaban en el atributo `Outputs`.  Para ello, MSBuild debía registrar estos elementos en caso de que las tareas los solicitaran más adelante en la compilación. Debido a que no existía ninguna manera de indicar qué destinos tenían salidas que los llamadores pudieran requerir, MSBuild acumulaba todos los elementos de todos los `Outputs` en todos los `Target` invocados. Esto ocasionaba problemas de escalado para las compilaciones que tenían un gran número de elementos de salida.

 Si el usuario especifica un `Returns` en cualquier elemento `Target` en un proyecto, solo los `Target` que tienen un atributo `Returns` registran esos elementos.

 Un `Target` puede contener los atributos `Outputs` y `Returns`.  `Outputs` se utiliza con `Inputs` para determinar si el destino está actualizado. `Returns`, si está presente, invalida el valor de `Outputs` para determinar qué elementos se devuelven a los llamadores.  Si `Returns` no está presente, a continuación, `Outputs` estará disponible para los llamadores, excepto en el caso descrito anteriormente.

 Antes de MSBuild 4, cada vez que un `Target` incluía varias referencias al mismo elemento en su `Outputs`, esos elementos duplicados se registraban. En compilaciones muy grandes que tenían un gran número de salidas y muchas interdependencias del proyecto, esto hacía que se perdiera una gran cantidad de memoria porque los elementos duplicados no tenían ninguna utilidad. Cuando el atributo `KeepDuplicateOutputs` se establece en `true`, estos duplicados se registran.

## <a name="example"></a>Ejemplo

 En el siguiente ejemplo de código se muestra un elemento `Target` que ejecuta la tarea `Csc`.

```xml
<Target Name="Compile" DependsOnTargets="Resources" Returns="$(TargetPath)">
    <Csc Sources="@(CSFile)"
          TargetType="library"
          Resources="@(CompiledResources)"
          EmitDebugInformation="$(includeDebugInformation)"
          References="@(Reference)"
          DebugType="$(debuggingType)" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Vea también

- [Destinos](../msbuild/msbuild-targets.md)
- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
