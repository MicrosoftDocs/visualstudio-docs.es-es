---
title: "C&#243;mo: Compilar versiones incrementalmente | Microsoft Docs"
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
  - "compilaciones incrementales"
  - "MSBuild, compilar de forma incremental"
  - "MSBuild, compilaciones incrementales"
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Compilar versiones incrementalmente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se compila un proyecto grande, es importante que los componentes que se compilaron previamente y que aún están actualizados no se recompilen.  Si todos los destinos se compilan cada vez, llevará más tiempo finalizar la compilación.  Para habilitar las compilaciones incrementales \(aquéllas en las que sólo se compilan los destinos no compilados con anterioridad o no actualizados\), [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] \([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\) compara las marcas de tiempo de los archivos de entrada con las de los archivos de salida y determina si debe omitir, compilar o recompilar parcialmente un destino.  Sin embargo, debe haber una asignación unívoca entre las entradas y resultados.  Se pueden utilizar las transformaciones para permitir que los destinos identifiquen esta asignación directa.  Para obtener más información sobre transformaciones, vea [Transformaciones](../msbuild/msbuild-transforms.md).  
  
## Especificar entradas y resultados  
 Es posible compilar un destino de forma incremental si se han especificado las entradas y los resultados en el archivo de proyecto.  
  
#### Para especificar las entradas y los resultados de un destino  
  
-   Utilice los atributos `Inputs` y `Outputs` del elemento `Target`.  Por ejemplo:  
  
    ```  
    <Target Name="Build"  
        Inputs="@(CSFile)"  
        Outputs="hello.exe">  
    ```  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] compara las marcas de tiempo de los archivos de entrada con las de los archivos de salida y determina si debe omitir, compilar o recompilar parcialmente un destino.  En el ejemplo siguiente, si algún archivo de la lista de elementos `@(CSFile)` es más reciente que el archivo hello.exe, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ejecutará el destino; de lo contrario, lo omitirá:  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Cuando las entradas y los resultados están especificados en un destino, puede suceder que cada resultado sólo se asigne a una entrada o que no exista ninguna asignación directa entre resultados y entradas.  Por ejemplo, en la tarea [Csc \(Tarea\)](../msbuild/csc-task.md) anterior, el resultado hello.exe no se puede asignar a una única entrada porque depende de todas ellas.  
  
> [!NOTE]
>  Un destino en el que no exista asignación directa entre entradas y resultados se compilará con más frecuencia que un destino en el que cada resultado sólo se puede asignar a una entrada. Esto se debe a que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] no puede determinar qué resultados necesitan recompilarse si algunas de las entradas han cambiado.  
  
 Las tareas en las que se puede identificar una asignación directa entre resultados y entradas, como la tarea [LC \(Tarea\)](../msbuild/lc-task.md), son más adecuadas para las compilaciones incrementales que las tareas como `Csc` y [Vbc](../msbuild/vbc-task.md), que producen un ensamblado de resultados a partir de una serie de entradas.  
  
## Ejemplo  
 En el ejemplo siguiente se usa un proyecto que compila archivos de Ayuda para un sistema de Ayuda hipotético.  El proyecto convierte archivos .txt de código fuente en archivos .content intermedios que, después, se combinan con archivos XML de metadatos para generar el archivo .help definitivo del sistema de Ayuda.  El proyecto usa las tareas hipotéticas siguientes:  
  
-   `GenerateContentFiles`: Convierte archivos .txt en archivos .content.  
  
-   `BuildHelp`: Combina archivos .content y archivos XML de metadatos para compilar el archivo .help final.  
  
 El proyecto usa transformaciones para crear una asignación unívoca entre las entradas y los resultados en la tarea `GenerateContentFiles`.  Para obtener más información, vea [Transformaciones](../msbuild/msbuild-transforms.md).  Asimismo, el elemento `Output` se establece para que utilice automáticamente los resultados de la tarea `GenerateContentFiles` como entradas para la tarea `BuildHelp`.  
  
 Este archivo de proyecto contiene los destinos `Convert` y `Build`.  Las tareas `GenerateContentFiles` y `BuildHelp` se colocan respectivamente en los destinos `Convert` y `Build` para que se pueda compilar cada destino incrementalmente.  Al usar el elemento `Output`, los resultados de la tarea `GenerateContentFiles` se colocan en la lista de elementos `ContentFile`, donde se pueden usar como entradas para la tarea `BuildHelp`.  Si usa el elemento `Output` de esta manera, proporcionará automáticamente los resultados de una tarea como entradas para otra tarea y no será necesario enumerar manualmente cada elemento o las listas de elementos de cada tarea.  
  
> [!NOTE]
>  Aunque el destino de `GenerateContentFiles` se puede compilar incrementalmente, todas las salidas de ese destino se requieren siempre como entradas para el destino de `BuildHelp`.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proporciona automáticamente todas las salidas de un destino como entradas para otro destino cuando se utiliza el elemento `Output`.  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <ItemGroup>  
        <TXTFile Include="*.txt"/>  
        <XMLFile Include="\metadata\*.xml"/>  
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
            MetadataFiles = "@(XMLFile)"  
            OutputFileName = "$(MSBuildProjectName).help"/>  
    </Target>  
</Project>  
```  
  
## Vea también  
 [Destinos](../msbuild/msbuild-targets.md)   
 [Elemento Target \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Transformaciones](../msbuild/msbuild-transforms.md)   
 [Csc \(Tarea\)](../msbuild/csc-task.md)   
 [Vbc \(Tarea\)](../msbuild/vbc-task.md)