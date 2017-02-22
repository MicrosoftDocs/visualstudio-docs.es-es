---
title: "C&#243;mo: Limpiar los resultados de una compilaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "directorios [.NET Framework], de elementos del resultado"
  - "Exec (tarea) [MSBuild]"
  - "MSBuild, depurar una compilación"
  - "resultado, quitar elementos"
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Limpiar los resultados de una compilaci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se limpian los resultados de una compilación, se eliminan todos los archivos intermedios y de salida, y sólo se conservan los archivos de proyecto y de componentes.  A partir de los archivos de proyecto y de componentes, se pueden compilar nuevas instancias de los archivos intermedios y de salida.  La biblioteca de tareas comunes proporcionada con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] incluye una tarea [Exec](../msbuild/exec-task.md) que se puede utilizar para ejecutar comandos de sistema.  Para obtener más información sobre la biblioteca de tareas, vea [Referencia de tareas](../msbuild/msbuild-task-reference.md).  
  
## Crear un directorio para los elementos de resultados  
 De forma predeterminada, el archivo .exe creado cuando se compila un proyecto se coloca en el mismo directorio que los archivos de proyecto y de código fuente.  Sin embargo, los elementos de resultados se crean, por lo general, en un directorio independiente.  
  
#### Para crear un directorio para los elementos de resultados  
  
1.  Utilice el elemento `Property` para definir la ubicación y el nombre del directorio.  Por ejemplo, cree un directorio con el nombre `BuiltApp` en el directorio que contiene los archivos de proyecto y de código fuente:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  Si el directorio no existe, utilice la tarea [MakeDir](../msbuild/makedir-task.md) para crearlo.  Por ejemplo:  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## Quitar los elementos de resultados  
 Antes de crear nuevas instancias de archivos intermedios y de salida, conviene borrar todas las instancias anteriores de estos archivos.  Utilice la tarea [RemoveDir](../msbuild/removedir-task.md) para eliminar un directorio y todos los archivos y directorios que contiene de un disco.  
  
#### Para quitar un directorio y todos los archivos que contiene  
  
-   Utilice la tarea `RemoveDir` para quitar el directorio.  Por ejemplo:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra un proyecto que contiene un nuevo destino, `Clean`, que utiliza la tarea `RemoveDir` para eliminar un directorio y todos los archivos y directorios que contiene.  También en este ejemplo, el destino `Compile` crea un directorio independiente para los elementos de resultados que se eliminan al limpiar la compilación.  
  
 `Compile` está definido como destino predeterminado, por lo que se utiliza automáticamente a menos que se especifique un destino o destinos diferentes.  El modificador de la línea de comandos **\/target** se utiliza para especificar un destino diferente.  Por ejemplo:  
  
 `msbuild <file name>.proj /target:Clean`  
  
 El modificador **\/target** se puede acortar en **\/t** y puede especificar más de un destino.  Por ejemplo, para utilizar el destino `Clean` y después el destino `Compile`, escriba:  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```  
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
  
## Vea también  
 [Exec \(Tarea\)](../msbuild/exec-task.md)   
 [MakeDir \(Tarea\)](../msbuild/makedir-task.md)   
 [RemoveDir \(Tarea\)](../msbuild/removedir-task.md)   
 [Csc \(Tarea\)](../msbuild/csc-task.md)   
 [Destinos](../msbuild/msbuild-targets.md)