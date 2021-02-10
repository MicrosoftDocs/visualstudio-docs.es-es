---
title: Hacer referencia al nombre o la ubicación del archivo de proyecto
description: Obtenga información sobre cómo usar las propiedades reservadas de MSBuild para hacer referencia a la ubicación o al nombre del archivo del proyecto sin que sea necesario crear sus propias propiedades.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c6527a4f54abf147d54e73c8f887b57b70ff4243
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914185"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Cómo: Hacer referencia al nombre o la ubicación del archivo de proyecto

Puede utilizar el nombre o la ubicación del proyecto en el archivo del proyecto sin tener que crear su propia propiedad. MSBuild proporciona propiedades reservadas que hacen referencia al nombre de archivo del proyecto y a otras propiedades relacionadas con el proyecto. Para obtener más información sobre las propiedades reservadas, vea [Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="use-the-project-properties"></a>Usar las propiedades de proyecto

 MSBuild proporciona algunas propiedades reservadas que se pueden usar en los archivos del proyecto sin tener que definirlas cada vez. Por ejemplo, la propiedad reservada `MSBuildProjectName` proporciona una referencia al nombre del archivo del proyecto. La propiedad reservada `MSBuildProjectDirectory` proporciona una referencia a la ubicación del archivo de proyecto.

#### <a name="to-use-the-project-properties"></a>Para usar las propiedades de proyecto

- Haga referencia a la propiedad en el archivo del proyecto con la notación $(), como haría con cualquier propiedad. Por ejemplo:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Una ventaja de utilizar una propiedad reservada es que cualquier cambio en el nombre del archivo del proyecto se incorpora automáticamente. La próxima vez que compile el proyecto, el archivo de salida tendrá el nuevo nombre, sin que tenga que hacer nada más.

  Para obtener más información sobre el uso de caracteres especiales en las referencias de archivo o proyecto, vea [Caracteres especiales de MSBuild](../msbuild/msbuild-special-characters.md).

> [!NOTE]
> Las propiedades reservadas no se pueden volver a definir en el archivo del proyecto.

## <a name="example-1"></a>Ejemplo 1

 El siguiente archivo del proyecto de ejemplo hace referencia al nombre del proyecto como una propiedad reservada para especificar el nombre de salida.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    DefaultTargets = "Compile">

    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
     </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using
        input files of type CSFile -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(MSBuildProjectName).exe" >
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the project -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example-2"></a>Ejemplo 2

 El siguiente archivo de proyecto de ejemplo usa la propiedad reservada `MSBuildProjectDirectory` para crear la ruta de acceso completa a un archivo en la ubicación del archivo de proyecto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

En el ejemplo se usa la sintaxis de la [función de propiedad](property-functions.md) para llamar al método estático de .NET Framework <xref:System.IO.Path.Combine*?displayProperty=fullName>.

## <a name="see-also"></a>Vea también

- [MSBuild](../msbuild/msbuild.md)
- [Propiedades reservadas y conocidas de MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
