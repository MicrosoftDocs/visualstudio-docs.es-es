---
title: Propiedades reservadas y conocidas de MSBuild | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ab4c18006834cc1bef6841864e42609e09bc3a1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585839"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Propiedades reservadas y conocidas de MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proporciona un conjunto de propiedades predefinidas que almacenan información sobre el archivo de proyecto y los archivos binarios de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Estas propiedades se evalúan igual que otras propiedades de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Por ejemplo, para utilizar la propiedad `MSBuildProjectFile` escribiría `$(MSBuildProjectFile)`.

 MSBuild utiliza los valores de la tabla siguiente para predefinir propiedades reservadas y conocidas. Las propiedades reservadas no se pueden invalidar, pero las propiedades conocidas se pueden invalidar con propiedades del entorno, propiedades globales o propiedades que se declaran en el archivo de proyecto con el mismo nombre.

## <a name="reserved-and-well-known-properties"></a>Propiedades reservadas y conocidas
 En la tabla siguiente se describen las propiedades predefinidas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

| Propiedad. | Reservadas o conocidas | Descripción |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Reservada | Ruta de acceso absoluta de la carpeta donde se encuentran los archivos binarios de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que se están usando (por ejemplo, *C:\Windows\Microsoft.Net\Framework\\\<númeroDeVersión>* ). Esta propiedad es útil si necesita hacer referencia a los archivos del directorio de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. |
| `MSBuildExtensionsPath` | Conocida | Introducida en .NET Framework 4: no hay ninguna diferencia entre los valores predeterminados de `MSBuildExtensionsPath` y de `MSBuildExtensionsPath32`. Puede establecer la variable de entorno `MSBUILDLEGACYEXTENSIONSPATH` en un valor distinto de null para habilitar el comportamiento del valor predeterminado de `MSBuildExtensionsPath` en versiones anteriores.<br /><br /> En .NET Framework 3.5 y versiones anteriores, el valor predeterminado de `MSBuildExtensionsPath` apunta a la ruta de la subcarpeta de MSBuild en la carpeta *\Archivos de programa\\* o *\Archivos de programa (x86)* , según el valor de bits del proceso actual. Por ejemplo, para un proceso de 32 bits en un equipo de 64 bits, esta propiedad apunta a la carpeta *\Archivos de programa (x86)* . Para un proceso de 64 bits en un equipo de 64 bits, esta propiedad apunta a la carpeta *\Archivos de programa*.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad.<br /><br /> Esta ubicación es un lugar útil para colocar archivos de destino personalizados. Por ejemplo, podría instalar los archivos de destino en *\Archivos de programa\MSBuild\MyFiles\Northwind.targets* y luego importarlos en archivos de proyecto con este código XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | Conocida | Ruta de acceso de la subcarpeta [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] en la carpeta *\Archivos de programa* o *\Archivos de programa (x86)* . La ruta de acceso siempre apunta a la carpeta de 32 bits *\Archivos de programa (x86)* en un equipo de 32 bits y a *\Archivos de programa* en un equipo de 64 bits. Vea también `MSBuildExtensionsPath` y `MSBuildExtensionsPath64`.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. |
| `MSBuildExtensionsPath64` | Conocida | Ruta de acceso de la subcarpeta [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] en la carpeta *\Archivos de programa*. En un equipo de 64 bits, esta ruta de acceso apunta siempre a la carpeta *\Archivos de programa*. Para un equipo de 32 bits, esta ruta de acceso está en blanco. Vea también `MSBuildExtensionsPath` y `MSBuildExtensionsPath32`.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. |
| `MSBuildLastTaskResult` | Reservada | `true` si la tarea anterior se completó sin errores (aunque hubiera advertencias) o `false` si la tarea anterior tuvo errores. Normalmente, cuando se produce un error en una tarea, el error es lo último que ocurre en ese proyecto. Por consiguiente, el valor de esta propiedad nunca es `false`, excepto en estos escenarios:<br /><br /> - Cuando el atributo `ContinueOnError` del [Elemento de tarea (MSBuild)](../msbuild/task-element-msbuild.md) está establecido en `WarnAndContinue` (o `true`) o `ErrorAndContinue`.<br /><br /> - Cuando `Target` tiene un [Elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) como elemento secundario. |
| `MSBuildNodeCount` | Reservada | Número máximo de procesos simultáneos que se usan al compilar. Este es el valor que ha especificado para **-maxcpucount** en la línea de comandos. Si ha especificado **-maxcpucount** sin especificar un valor, `MSBuildNodeCount` especifica el número de procesadores del equipo. Para obtener más información, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md) y [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). |
| `MSBuildProgramFiles32` | Reservada | Ubicación de la carpeta de programas de 32 bits; por ejemplo, *C:\Archivos de programa (x86)* .<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. |
| `MSBuildProjectDefaultTargets` | Reservada | Lista completa de destinos especificados en el atributo `DefaultTargets` del elemento `Project`. Por ejemplo, el siguiente elemento `Project` tendría un valor de propiedad `MSBuildDefaultTargets` de `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Reservada | Ruta de acceso absoluta del directorio en el que se encuentra el archivo de proyecto, por ejemplo, *C:\MyCompany\MyProduct*.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. |
| `MSBuildProjectDirectoryNoRoot` | Reservada | Valor de la propiedad `MSBuildProjectDirectory`, sin incluir la unidad raíz.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. |
| `MSBuildProjectExtension` | Reservada | Extensión de nombre de archivo del archivo de proyecto, incluido el punto; por ejemplo, *.proj*. |
| `MSBuildProjectFile` | Reservada | Nombre de archivo completo del archivo de proyecto, incluida la extensión de nombre de archivo; por ejemplo, *MyApp.proj*. |
| `MSBuildProjectFullPath` | Reservada | Ruta de acceso absoluta y nombre de archivo completo del archivo de proyecto, incluida la extensión de nombre de archivo; por ejemplo, *C:\MyCompany\MyProduct\MyApp.proj*. |
| `MSBuildProjectName` | Reservada | Nombre de archivo del archivo de proyecto sin la extensión de nombre de archivo; por ejemplo, *MyApp*. |
| `MSBuildRuntimeType` | Reservada | El tipo del runtime que se está ejecutando actualmente. Se presentó en MSBuild 15. El valor puede no estar definido (antes de MSBuild 15): `Full` indica que MSBuild se está ejecutando en la versión de escritorio de .NET Framework, `Core` indica que MSBuild se está ejecutando en .NET Core (por ejemplo, en `dotnet build`) o `Mono` indica que MSBuild se está ejecutando en Mono. |
| `MSBuildStartupDirectory` | Reservada | Ruta de acceso absoluta de la carpeta donde se llama a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Con esta propiedad puede compilar todo lo que hay debajo de un punto específico de un árbol de proyecto sin crear archivos *\<dirs>.proj* en cada directorio. En su lugar, tiene solo un proyecto, por ejemplo, *c:\traversal.proj*, como se muestra aquí:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Para compilar en cualquier punto del árbol, escriba:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> No incluya la barra diagonal inversa final en esta propiedad. |
| `MSBuildThisFile` | Reservada | Parte de nombre de archivo y extensión de archivo de `MSBuildThisFileFullPath`. |
| `MSBuildThisFileDirectory` | Reservada | Parte de directorio de `MSBuildThisFileFullPath`.<br /><br /> Incluya la barra diagonal inversa final de la ruta. |
| `MSBuildThisFileDirectoryNoRoot` | Reservada | Parte del directorio de `MSBuildThisFileFullPath`, sin incluir la unidad raíz.<br /><br /> Incluya la barra diagonal inversa final de la ruta. |
| `MSBuildThisFileExtension` | Reservada | Parte de la extensión de nombre de archivo de `MSBuildThisFileFullPath`. |
| `MSBuildThisFileFullPath` | Reservada | Ruta de acceso absoluta del archivo de proyecto o de destinos que contiene el destino que se está ejecutando.<br /><br /> Sugerencia: Puede especificar una ruta de acceso relativa en un archivo de destinos relativa al archivo de destinos y no relativa al archivo de proyecto original. |
| `MSBuildThisFileName` | Reservada | Parte de nombre de archivo de `MSBuildThisFileFullPath`, sin la extensión de nombre de archivo. |
| `MSBuildToolsPath` | Reservada | Ruta de acceso de instalación de la versión de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que se asocia al valor de `MSBuildToolsVersion`.<br /><br /> No incluya la barra diagonal inversa final de la ruta.<br /><br /> Esta propiedad no se puede invalidar. |
| `MSBuildToolsVersion` | Reservada | Versión del conjunto de herramientas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que se utilizará para compilar el proyecto.<br /><br /> Nota: Un conjunto de herramientas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] consta de tareas, destinos y herramientas que se utilizan para compilar una aplicación. Las herramientas incluyen compiladores como *csc.exe* y *vbc.exe*. Para obtener más información, vea [Conjunto de herramientas de MSBuild (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) y [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md). |
| `MSBuildVersion` | Reservada | La versión de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que se usa para compilar el proyecto. <br /><br/> Esta propiedad no se puede invalidar, de lo contrario, se devuelve el mensaje de error `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.`. |

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
