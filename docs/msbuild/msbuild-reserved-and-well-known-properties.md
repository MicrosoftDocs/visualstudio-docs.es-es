---
title: Propiedades reservadas y conocidas de MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords: MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: "29"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 136e488f78090211f4c63f685338d61556982b9d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Propiedades reservadas y conocidas de MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proporciona un conjunto de propiedades predefinidas que almacenan información sobre el archivo de proyecto y los archivos binarios de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Estas propiedades se evalúan igual que otras propiedades de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Por ejemplo, para utilizar la propiedad `MSBuildProjectFile` escribiría `$(MSBuildProjectFile)`.  
  
 MSBuild utiliza los valores de la tabla siguiente para predefinir propiedades reservadas y conocidas. Las propiedades reservadas no se pueden invalidar, pero las propiedades conocidas se pueden invalidar con propiedades del entorno, propiedades globales o propiedades que se declaran en el archivo de proyecto con el mismo nombre.  
  
## <a name="reserved-and-well-known-properties"></a>Propiedades reservadas y conocidas  
 En la tabla siguiente se describen las propiedades predefinidas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
|Property|Description|Reservadas o conocidas|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Ruta de acceso absoluta de la carpeta donde se encuentran los archivos binarios de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que se están utilizando actualmente (por ejemplo, C:\Windows\Microsoft.Net\Framework\\*versionNumber*). Esta propiedad es útil si necesita hacer referencia a los archivos del directorio de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].<br /><br /> No incluya la barra diagonal inversa final en esta propiedad.|Reservada|  
|`MSBuildExtensionsPath`|Introducida en .NET Framework 4: no hay ninguna diferencia entre los valores predeterminados de `MSBuildExtensionsPath` y de `MSBuildExtensionsPath32`. Puede establecer la variable de entorno `MSBUILDLEGACYEXTENSIONSPATH` en un valor distinto de null para habilitar el comportamiento del valor predeterminado de `MSBuildExtensionsPath` en versiones anteriores.<br /><br /> En .NET Framework 3.5 y en versiones anteriores, el valor predeterminado de `MSBuildExtensionsPath` apunta a la ruta de la subcarpeta de MSBuild bajo la carpeta \Archivos de programa\ o \Archivos de programa (x86), según el valor de bits del proceso actual. Por ejemplo, para un proceso de 32 bits en un equipo de 64 bits, esta propiedad apunta a la carpeta \Archivos de programa (x86). Para un proceso de 64 bits en un equipo de 64 bits, esta propiedad apunta a la carpeta \Archivos de programa.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad.<br /><br /> Esta ubicación es un lugar útil para colocar archivos de destino personalizados. Por ejemplo, podría instalar archivos de destino en \Archivos de programa\MSBuild\MisArchivos\Northwind.targets y, a continuación, importarlos en archivos de proyecto con este código XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|Conocida|  
|`MSBuildExtensionsPath32`|Ruta de acceso de la subcarpeta [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bajo la carpeta \Archivos de programa\ o \Archivos de programa (x86). Esta ruta de acceso siempre apunta a la carpeta \Archivos de programa de 32 bits en un equipo de 32 bits y a \Archivos de programa (x86) en un equipo de 64 bits. Vea también `MSBuildExtensionsPath` y `MSBuildExtensionsPath64`.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad.|Conocida|  
`MSBuildExtensionsPath64`|Ruta de acceso de la subcarpeta [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] en la carpeta \Archivos de programa. Para un equipo de 64 bits, esta ruta de acceso apunta siempre a la carpeta \Archivos de programa. Para un equipo de 32 bits, esta ruta de acceso está en blanco. Vea también `MSBuildExtensionsPath` y `MSBuildExtensionsPath32`.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad.|Conocida|  
|`MSBuildLastTaskResult`|`true` si la tarea anterior se completó sin errores (aunque hubiera advertencias) o `false` si la tarea anterior tuvo errores. Normalmente, cuando se produce un error en una tarea, el error es lo último que ocurre en ese proyecto. Por consiguiente, el valor de esta propiedad nunca es `false`, excepto en estos escenarios:<br /><br /> - Cuando el atributo `ContinueOnError` del [elemento Task (MSBuild)](../msbuild/task-element-msbuild.md) está establecido en `WarnAndContinue` (o `true`) o `ErrorAndContinue`.<br /><br /> - Cuando el `Target` tiene un [elemento OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) como un elemento secundario.|Reservada|  
|`MSBuildNodeCount`|Número máximo de procesos simultáneos que se usan al compilar. Este es el valor que ha especificado para **/maxcpucount** en la línea de comandos. Si ha especificado **/maxcpucount** sin especificar un valor, `MSBuildNodeCount` especifica el número de procesadores del equipo. Para obtener más información, consulte [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md) y [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Reservada|  
|`MSBuildProgramFiles32`|Ubicación de la carpeta de programas de 32 bits; por ejemplo, `C:\Program Files (x86)`.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad.|Reservada|  
|`MSBuildProjectDefaultTargets`|Lista completa de destinos especificados en el atributo `DefaultTargets` del elemento `Project`. Por ejemplo, el siguiente elemento `Project` tendría un valor de propiedad `MSBuildDefaultTargets` de `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >`|Reservada|  
|`MSBuildProjectDirectory`|Ruta de acceso absoluta al directorio en el que está ubicado el archivo de proyecto; por ejemplo, `C:\MyCompany\MyProduct`.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad.|Reservada|  
|`MSBuildProjectDirectoryNoRoot`|Valor de la propiedad `MSBuildProjectDirectory`, sin incluir la unidad raíz.<br /><br /> No incluya la barra diagonal inversa final en esta propiedad.|Reservada|  
|`MSBuildProjectExtension`|Extensión de nombre de archivo del archivo de proyecto, incluido el punto; por ejemplo, .proj.|Reservada|  
|`MSBuildProjectFile`|Nombre de archivo completo del archivo de proyecto, incluida la extensión de nombre de archivo; por ejemplo, MiApl.proj.|Reservada|  
|`MSBuildProjectFullPath`|Ruta de acceso absoluta y nombre de archivo completo del archivo de proyecto, incluida la extensión de nombre de archivo; por ejemplo, C:\MiEmpresa\MiProducto\MiApl.proj.|Reservada|  
|`MSBuildProjectName`|Nombre de archivo del archivo de proyecto sin la extensión de nombre de archivo; por ejemplo, MiApl.|Reservada|  
|`MSBuildRuntimeType`|El tipo del runtime que se está ejecutando actualmente. Se presentó en MSBuild 15. El valor puede no estar definido (antes de MSBuild 15), `Full` indica que MSBuild está ejecutándose en la versión de .NET Framework de escritorio, `Core` indica que MSBuild está ejecutándose en .NET Core o `Mono` indica que MSBuild está ejecutándose en Mono.|Reservada|  
|`MSBuildStartupDirectory`|Ruta de acceso absoluta de la carpeta donde se llama a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Con esta propiedad, puede compilar todo lo que hay debajo de un punto específico en un árbol de proyecto sin crear archivos dirs.proj en cada directorio. En su lugar, tiene solo un proyecto, por ejemplo, c:\traversal.proj, como se muestra aquí:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Para compilar en cualquier punto del árbol, escriba:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> No incluya la barra diagonal inversa final en esta propiedad.|Reservada|  
|`MSBuildThisFile`|Parte de nombre de archivo y extensión de archivo de `MSBuildThisFileFullPath`.|Reservada|  
|`MSBuildThisFileDirectory`|Parte de directorio de `MSBuildThisFileFullPath`.<br /><br /> Incluya la barra diagonal inversa final de la ruta.|Reservada|  
|`MSBuildThisFileDirectoryNoRoot`|Parte del directorio de `MSBuildThisFileFullPath`, sin incluir la unidad raíz.<br /><br /> Incluya la barra diagonal inversa final de la ruta.|Reservada|  
|`MSBuildThisFileExtension`|Parte de la extensión de nombre de archivo de `MSBuildThisFileFullPath`.|Reservada|  
|`MSBuildThisFileFullPath`|Ruta de acceso absoluta del archivo de proyecto o de destinos que contiene el destino que se está ejecutando.<br /><br /> Consejo: Puede especificar una ruta de acceso relativa en un archivo de destinos relativa al archivo de destinos y no relativa al archivo del proyecto original.|Reservada|  
|`MSBuildThisFileName`|Parte de nombre de archivo de `MSBuildThisFileFullPath`, sin la extensión de nombre de archivo.|Reservada|  
|`MSBuildToolsPath`|Ruta de acceso de instalación de la versión de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que se asocia al valor de `MSBuildToolsVersion`.<br /><br /> No incluya la barra diagonal inversa final de la ruta.<br /><br /> Esta propiedad no se puede invalidar.|Reservada|  
|`MSBuildToolsVersion`|Versión del conjunto de herramientas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que se utilizará para compilar el proyecto.<br /><br /> Nota: Un conjunto de herramientas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] consta de tareas, destinos y herramientas que se utilizan para compilar una aplicación. Las herramientas incluyen compiladores como csc.exe y vbc.exe. Para obtener más información, consulte [Conjunto de herramientas (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md) y [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md).|Reservada|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md) [Propiedades de MSBuild](../msbuild/msbuild-properties.md)