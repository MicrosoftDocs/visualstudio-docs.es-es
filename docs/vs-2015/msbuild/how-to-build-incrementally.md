---
title: 'Cómo: Compilar de forma incremental | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, incremental builds
- incremental builds
- MSBuild, building incrementally
ms.assetid: 8d82d7d8-a2f1-4df6-9d2f-80b9e0cb3ac3
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 88ad4f984af2be6884005c5ec3c7dec4d7b5c6aa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844629"
---
# <a name="how-to-build-incrementally"></a>Cómo: Compilar versiones incrementalmente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Cuando se compila un proyecto grande, es importante que los componentes que se compilaron previamente y que aún están actualizados no se recompilen. Si todos los destinos se compilan cada vez, llevará más tiempo finalizar la compilación. Para habilitar las compilaciones incrementales (aquellas en las que solo se compilan los destinos no compilados con anterioridad o no actualizados), [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) compara las marcas de tiempo de los archivos de entrada con las de los archivos de salida y determina si debe omitir, compilar o recompilar parcialmente un destino. En cambio, debe haber una asignación unívoca entre las entradas y resultados. Se pueden usar las transformaciones para permitir que los destinos identifiquen esta asignación directa. Para obtener más información sobre transformaciones, vea [Transformaciones](../msbuild/msbuild-transforms.md).  
  
## <a name="specifying-inputs-and-outputs"></a>Especificar entradas y resultados  
 Es posible compilar un destino de forma incremental si se han especificado las entradas y los resultados en el archivo de proyecto.  
  
#### <a name="to-specify-inputs-and-outputs-for-a-target"></a>Para especificar las entradas y los resultados de un destino  
  
- Use los atributos `Inputs` y `Outputs` del elemento `Target`. Por ejemplo:  
  
  ```  
  <Target Name="Build"  
      Inputs="@(CSFile)"  
      Outputs="hello.exe">  
  ```  
  
  [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] compara las marcas de tiempo de los archivos de entrada con las de los archivos de salida y determina si debe omitir, compilar o recompilar parcialmente un destino. En el ejemplo siguiente, si algún archivo de la lista de elementos `@(CSFile)` es más reciente que el archivo hello.exe, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ejecutará el destino; de lo contrario, lo omitirá:  
  
```  
<Target Name="Build"   
    Inputs="@(CSFile)"   
    Outputs="hello.exe">  
  
    <Csc  
        Sources="@(CSFile)"   
        OutputAssembly="hello.exe"/>  
</Target>  
```  
  
 Cuando las entradas y los resultados están especificados en un destino, puede suceder que cada resultado solo se asigne a una entrada o que no exista ninguna asignación directa entre resultados y entradas. En el anterior [Csc (tarea)](../msbuild/csc-task.md), por ejemplo, la salida, hello.exe, no se puede asignar a una única entrada: depende de todas ellas.  
  
> [!NOTE]
>  Un destino en el que no exista asignación directa entre entradas y resultados se compilará con más frecuencia que un destino en el que cada resultado solo se puede asignar a una entrada. Esto se debe a que [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] no puede determinar qué resultados necesitan recompilarse si algunas de las entradas han cambiado.  
  
 Las tareas en las que se puede identificar una asignación directa entre resultados y entradas, como la [tarea LC](../msbuild/lc-task.md), son más adecuadas para las compilaciones incrementales que las tareas como `Csc` y [Vbc](../msbuild/vbc-task.md), que producen un ensamblado de resultados a partir de una serie de entradas.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa un proyecto que compila archivos de Ayuda para un sistema de Ayuda hipotético. El proyecto convierte archivos .txt de código fuente en archivos .content intermedios que, después, se combinan con archivos XML de metadatos para generar el archivo .help definitivo del sistema de Ayuda. El proyecto usa las tareas hipotéticas siguientes:  
  
- `GenerateContentFiles`: Convierte archivos .txt en archivos .content.  
  
- `BuildHelp`: Combina archivos .content y archivos XML de metadatos para compilar el archivo .help final.  
  
  El proyecto usa transformaciones para crear una asignación unívoca entre las entradas y los resultados en la tarea `GenerateContentFiles`. Para obtener más información, consulte [Transformaciones](../msbuild/msbuild-transforms.md). Además, el elemento `Output` se establece para que use automáticamente los resultados de la tarea `GenerateContentFiles` como entradas para la tarea `BuildHelp`.  
  
  Este archivo de proyecto contiene los destinos `Convert` y `Build`. Las tareas `GenerateContentFiles` y `BuildHelp` se colocan respectivamente en los destinos `Convert` y `Build` para que se pueda compilar cada destino incrementalmente. Al usar el elemento `Output`, los resultados de la tarea `GenerateContentFiles` se colocan en la lista de elementos `ContentFile`, donde se pueden usar como entradas para la tarea `BuildHelp`. Si usa el elemento `Output` de esta manera, proporcionará automáticamente los resultados de una tarea como entradas para otra tarea y no será necesario enumerar manualmente cada elemento o las listas de elementos de cada tarea.  
  
> [!NOTE]
>  Aunque el destino de `GenerateContentFiles` se puede compilar incrementalmente, todas las salidas de ese destino se requieren siempre como entradas para el destino de `BuildHelp`. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] proporciona automáticamente todas las salidas de un destino como entradas para otro destino cuando se usa el elemento `Output`.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Destinos](../msbuild/msbuild-targets.md)   
 [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Transformaciones](../msbuild/msbuild-transforms.md)   
 [Csc (tarea)](../msbuild/csc-task.md)   
 [Tarea Vbc](../msbuild/vbc-task.md)



