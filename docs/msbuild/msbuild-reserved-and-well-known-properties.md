---
title: Propiedades reservadas y conocidas de MSBuild | Microsoft Docs
description: Obtenga información sobre las propiedades reservadas y conocidas de MSBuild, propiedades predefinidas que almacenan información sobre el archivo de proyecto y los archivos binarios de MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2edfd4b9391beed5c379817c55871759ff02eec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384933"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Propiedades reservadas y conocidas de MSBuild

MSBuild proporciona un conjunto de propiedades predefinidas que almacenan información sobre el archivo de proyecto y los archivos binarios de MSBuild. Estas propiedades se evalúan igual que otras propiedades de MSBuild. Por ejemplo, para utilizar la propiedad `MSBuildProjectFile` escribiría `$(MSBuildProjectFile)`.

 MSBuild utiliza los valores de la tabla siguiente para predefinir propiedades reservadas y conocidas. Las propiedades reservadas no se pueden invalidar, pero las propiedades conocidas se pueden invalidar con propiedades del entorno, propiedades globales o propiedades que se declaran en el archivo de proyecto con el mismo nombre.

## <a name="reserved-and-well-known-properties"></a>Propiedades reservadas y conocidas

En la tabla de esta sección se muestran las propiedades predefinidas de MSBuild. La columna de ejemplo de la tabla se relaciona con el siguiente archivo de proyecto de ejemplo (se supone que se encuentra en `C:\Source\Repos\ConsoleApp1\ConsoleApp1`) y muestra los valores que tienen estas propiedades cuando se accede a ellas en el archivo de proyecto, cuando MSBuild se invoca sin opciones de línea de comandos especiales, con una compilación de versión preliminar instalada de Visual Studio 2019, versión 16.7.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

| Propiedad. | Reservadas o conocidas | Descripción | Ejemplo |
|----------------------------------|------------------------| - | - |
| `MSBuildBinPath` | Reservada | La ruta de acceso absoluta de la carpeta donde se encuentran los archivos binarios de MSBuild que se usan (por ejemplo, *C:\Windows\Microsoft.Net\Framework\\\<versionNumber>* ). Esta propiedad es útil si necesita hacer referencia a los archivos del directorio de MSBuild.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildExtensionsPath` | Conocida | Introducida en .NET Framework 4: no hay ninguna diferencia entre los valores predeterminados de `MSBuildExtensionsPath` y de `MSBuildExtensionsPath32`. Puede establecer la variable de entorno `MSBUILDLEGACYEXTENSIONSPATH` en un valor distinto de null para habilitar el comportamiento del valor predeterminado de `MSBuildExtensionsPath` en versiones anteriores.<br /><br /> En .NET Framework 3.5 y versiones anteriores, el valor predeterminado de `MSBuildExtensionsPath` apunta a la ruta de la subcarpeta de MSBuild en la carpeta *\Archivos de programa\\* o *\Archivos de programa (x86)* , según el valor de bits del proceso actual. Por ejemplo, para un proceso de 32 bits en un equipo de 64 bits, esta propiedad apunta a la carpeta *\Archivos de programa (x86)* . Para un proceso de 64 bits en un equipo de 64 bits, esta propiedad apunta a la carpeta *\Archivos de programa*.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad.<br /><br /> Esta ubicación es un lugar útil para colocar archivos de destino personalizados. Por ejemplo, podría instalar los archivos de destino en *\Archivos de programa\MSBuild\MyFiles\Northwind.targets* y luego importarlos en archivos de proyecto con este código XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath32` | Conocida | Ruta de acceso de la subcarpeta MSBuild en la carpeta *\Archivos de programa* o *\Archivos de programa (x86)* . La ruta de acceso siempre apunta a la carpeta de 32 bits *\Archivos de programa (x86)* en un equipo de 32 bits y a *\Archivos de programa* en un equipo de 64 bits. Vea también `MSBuildExtensionsPath` y `MSBuildExtensionsPath64`.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath64` | Conocida | Ruta de acceso de la subcarpeta MSBuild en la carpeta *\Archivos de programa*. En un equipo de 64 bits, esta ruta de acceso apunta siempre a la carpeta *\Archivos de programa*. Para un equipo de 32 bits, esta ruta de acceso está en blanco. Vea también `MSBuildExtensionsPath` y `MSBuildExtensionsPath32`.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. | `C:\Program Files\MSBuild`|
| `MSBuildInteractive` | Reservada | `true` si MSBuild se ejecuta de forma interactiva y permite entrada de usuario. Este valor se controla mediante la opción de línea de comandos `-interactive`. | `false` |
| `MSBuildLastTaskResult` | Reservada | `true` si la tarea anterior se completó sin errores (aunque hubiera advertencias) o `false` si la tarea anterior tuvo errores. Normalmente, cuando se produce un error en una tarea, el error es lo último que ocurre en ese proyecto. Por consiguiente, el valor de esta propiedad nunca es `false`, excepto en estos escenarios:<br /><br /> - Cuando el atributo `ContinueOnError` del [Elemento de tarea (MSBuild)](../msbuild/task-element-msbuild.md) está establecido en `WarnAndContinue` (o `true`) o `ErrorAndContinue`.<br /><br /> - Cuando `Target` tiene un [Elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) como elemento secundario. | `true` |
| `MSBuildNodeCount` | Reservada | Número máximo de procesos simultáneos que se usan al compilar. Este es el valor que ha especificado para **-maxcpucount** en la línea de comandos. Si ha especificado **-maxcpucount** sin especificar un valor, `MSBuildNodeCount` especifica el número de procesadores del equipo. Para obtener más información, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md) y [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). | 1 |
| `MSBuildProgramFiles32` | Reservada | Ubicación de la carpeta de programas de 32 bits; por ejemplo, *C:\Archivos de programa (x86)* .<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. | `C:\Program Files (x86)`|
| `MSBuildProjectDefaultTargets` | Reservada | Lista completa de destinos especificados en el atributo `DefaultTargets` del elemento `Project`. Por ejemplo, el siguiente elemento `Project` tendría un valor de propiedad `MSBuildDefaultTargets` de `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >` | `Build`|
| `MSBuildProjectDirectory` | Reservada | Ruta de acceso absoluta del directorio en el que se encuentra el archivo de proyecto, por ejemplo, *C:\MyCompany\MyProduct*.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. | `C:\Source\Repos\ConsoleApp1\ConsoleApp1` |
| `MSBuildProjectDirectoryNoRoot` | Reservada | Valor de la propiedad `MSBuildProjectDirectory`, sin incluir la unidad raíz.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. | `Source\Repos\ConsoleApp1\ConsoleApp1`|
| `MSBuildProjectExtension` | Reservada | Extensión de nombre de archivo del archivo de proyecto, incluido el punto; por ejemplo, *.proj*. | `.csproj`|
| `MSBuildProjectFile` | Reservada | Nombre de archivo completo del archivo de proyecto, incluida la extensión de nombre de archivo; por ejemplo, *MyApp.proj*. | `ConsoleApp1.csproj`|
| `MSBuildProjectFullPath` | Reservada | Ruta de acceso absoluta y nombre de archivo completo del archivo de proyecto, incluida la extensión de nombre de archivo; por ejemplo, *C:\MyCompany\MyProduct\MyApp.proj*. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj`|
| `MSBuildProjectName` | Reservada | Nombre de archivo del archivo de proyecto sin la extensión de nombre de archivo; por ejemplo, *MyApp*. | `ConsoleApp1` |
| `MSBuildRuntimeType` | Reservada | El tipo del runtime que se está ejecutando actualmente. Se presentó en MSBuild 15. El valor puede no estar definido (antes de MSBuild 15): `Full` indica que MSBuild se está ejecutando en la versión de escritorio de .NET Framework, `Core` indica que MSBuild se está ejecutando en .NET Core (por ejemplo, en `dotnet build`) o `Mono` indica que MSBuild se está ejecutando en Mono. | `Full` |
| `MSBuildStartupDirectory` | Reservada | Ruta de acceso absoluta de la carpeta donde se llama a MSBuild. Con esta propiedad puede compilar todo lo que hay debajo de un punto específico de un árbol de proyecto sin crear archivos *\<dirs>.proj* en cada directorio. En su lugar, tiene solo un proyecto, por ejemplo, *c:\traversal.proj*, como se muestra aquí:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Para compilar en cualquier punto del árbol, escriba:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. | `c:\Source\Repos\ConsoleApp1` |
| `MSBuildThisFile` | Reservada | Parte de nombre de archivo y extensión de archivo de `MSBuildThisFileFullPath`. | `ConsoleApp1.csproj` |
| `MSBuildThisFileDirectory` | Reservada | Parte de directorio de `MSBuildThisFileFullPath`.<br /><br /> Incluya la barra diagonal inversa final de la ruta. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileDirectoryNoRoot` | Reservada | Parte del directorio de `MSBuildThisFileFullPath`, sin incluir la unidad raíz.<br /><br /> Incluya la barra diagonal inversa final de la ruta. | `Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileExtension` | Reservada | Parte de la extensión de nombre de archivo de `MSBuildThisFileFullPath`. | `.csproj` |
| `MSBuildThisFileFullPath` | Reservada | Ruta de acceso absoluta del archivo de proyecto o de destinos que contiene el destino que se está ejecutando.<br /><br /> Sugerencia: Puede especificar una ruta de acceso relativa en un archivo de destinos relativa al archivo de destinos y no relativa al archivo de proyecto original. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj` |
| `MSBuildThisFileName` | Reservada | Parte de nombre de archivo de `MSBuildThisFileFullPath`, sin la extensión de nombre de archivo. | `ConsoleApp1` |
| `MSBuildToolsPath` | Reservada | Ruta de acceso de instalación de la versión de MSBuild que se asocia al valor de `MSBuildToolsVersion`.<br /><br /> No incluya la barra diagonal inversa final de la ruta.<br /><br /> Esta propiedad no se puede invalidar. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildToolsVersion` | Reservada | Versión del conjunto de herramientas de MSBuild que se utilizará para compilar el proyecto.<br /><br /> Nota: Un conjunto de herramientas de MSBuild consta de tareas, destinos y herramientas que se utilizan para compilar una aplicación. Las herramientas incluyen compiladores como *csc.exe* y *vbc.exe*. Para obtener más información, vea [Conjunto de herramientas de MSBuild (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) y [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md). | `Current` |
| `MSBuildVersion` | Reservada | La versión de MSBuild que se usa para compilar el proyecto. <br /><br/> Esta propiedad no se puede invalidar, de lo contrario, se devuelve el mensaje de error `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.`. | 16.11.0 |
| `MSBuildAssemblyVersion` | Reservado | La versión de los ensamblados de MSBuild que se usan para compilar el proyecto. | 16.0 |
| `MSBuildFileVersion` | Reservado | La versión de cuatro partes de los ensamblados de MSBuild que se usan para compilar el proyecto. | 16.11.0.30701 |
| `MSBuildSemanticVersion` | Reservado | La versión de semver 2.0 completa de los ensamblados de MSBuild que se usan para compilar el proyecto. | 16.11.0-preview-21302-05+5e37cc992 |

## <a name="names-that-conflict-with-msbuild-elements"></a>Nombres en conflicto con elementos de MSBuild

Aparte de lo anterior, los nombres relativos a elementos del lenguaje MSBuild no se pueden usar en las propiedades, elementos o metadatos de elementos definidos por el usuario:

* VisualStudioProject
* Destino
* PropertyGroup
* Salida
* ItemGroup
* UsingTask
* ProjectExtensions
* OnError
* ImportGroup
* Elegir
* Cuando
* Otherwise

## <a name="see-also"></a>Vea también

- [Referencia de MSBuild](../msbuild/msbuild-reference.md)

- [Propiedades de MSBuild](../msbuild/msbuild-properties.md)
