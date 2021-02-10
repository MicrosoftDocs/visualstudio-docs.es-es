---
title: 'Cómo: Limpiar una compilación | Microsoft Docs'
description: Obtenga información sobre cómo usar MSBuild para limpiar una compilación, eliminando todos los archivos intermedios y de salida y dejando solo los archivos de proyecto y de componentes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6c0beb70379d8b79a3e1826ba74f34202eea19f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914451"
---
# <a name="how-to-clean-a-build"></a>Cómo: Limpiar una compilación

Cuando se limpia una compilación, se eliminan todos los archivos intermedios y de salida, de modo que solo queden los archivos de proyecto y de componentes. A partir de los archivos de proyecto y de componentes, se pueden compilar nuevas instancias de archivos intermedios y de salida. 

## <a name="create-a-directory-for-output-items"></a>Crear un directorio de elementos de salida

 De forma predeterminada, el archivo *.exe* que se crea cuando se compila un proyecto, se coloca en el mismo directorio que los archivos de proyecto y de código fuente. En cambio, los elementos de salida suelen crearse en un directorio independiente.

### <a name="to-create-a-directory-for-output-items"></a>Para crear un directorio para los elementos de salida

1. Use el elemento `Property` para definir la ubicación y el nombre del directorio. Por ejemplo, cree un directorio denominado *BuiltApp* en el directorio que contiene los archivos de proyecto y de código fuente:

     `<builtdir>BuiltApp</builtdir>`

2. Use la tarea [MakeDir](../msbuild/makedir-task.md) para crear el directorio, si este no existe. Por ejemplo:

     ```xml
     <MakeDir Directories = "$(builtdir)"
      Condition = "!Exists('$(builtdir)')" />
     ```

## <a name="remove-the-output-items"></a>Quitar los elementos de salida

 Antes de crear instancias de los archivos intermedios y de salida, puede que le interese borrar todas las instancias anteriores de los archivos intermedios y de salida. Use la tarea [RemoveDir](../msbuild/removedir-task.md) para eliminar de un disco un directorio y todos los archivos y directorios que contiene.

#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Para quitar un directorio y todos los archivos que contiene

- Use la tarea `RemoveDir` para quitar el directorio. Por ejemplo:

     `<RemoveDir Directories="$(builtdir)" />`

## <a name="example"></a>Ejemplo

 El siguiente proyecto de ejemplo de código contiene un nuevo destino, `Clean`, que usa la tarea `RemoveDir` para eliminar un directorio y todos los archivos y directorios que contiene. También en este ejemplo, el destino `Compile` crea un directorio independiente para los elementos de salida que se eliminan cuando se limpia la compilación.

 `Compile` se define como el destino predeterminado y, por tanto, se usa automáticamente a menos que se especifiquen otros destinos. Use el modificador de la línea de comandos **-target** para especificar un destino diferente. Por ejemplo:

 `msbuild <file name>.proj -target:Clean`

 El modificador **-target** se puede abreviar como **-t** y puede especificar más de un destino. Por ejemplo, para usar el destino `Clean` y, luego, el destino `Compile`, escriba:

 `msbuild <file name>.proj -t:Clean;Compile`

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <PropertyGroup>
        <!-- Set the application name as a property -->
        <name>HelloWorldCS</name>

        <!-- Set the output folder as a property -->
        <builtdir>BuiltApp</builtdir>
    </PropertyGroup>

    <ItemGroup>
        <!-- Specify the inputs by type and file name -->
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Check whether an output folder exists and create
        one if necessary -->
        <MakeDir Directories = "$(builtdir)"
            Condition = "!Exists('$(builtdir)')" />

        <!-- Run the Visual C# compiler -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(BuiltDir)\$(appname).exe">
            <Output TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>

        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>

    <Target Name = "Clean">
        <RemoveDir Directories="$(builtdir)" />
    </Target>
</Project>
```

## <a name="see-also"></a>Consulte también

- [MakeDir (tarea)](../msbuild/makedir-task.md)
- [Tarea RemoveDir](../msbuild/removedir-task.md)
- [Tarea Csc](../msbuild/csc-task.md)
- [Destinos](../msbuild/msbuild-targets.md)
