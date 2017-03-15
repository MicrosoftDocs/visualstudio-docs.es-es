---
title: "Procesamiento por lotes de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "procesar por lotes [MSBuild]"
  - "MSBuild, procesar por lotes"
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Procesamiento por lotes de MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tiene la capacidad de dividir las listas de elementos en distintas categorías, o lotes, basándose en los metadatos de estos elementos, y luego ejecutar un destino o una tarea una vez con cada lote.  
  
## Procesamiento por lotes de tareas  
 El procesamiento por lotes de tareas permite simplificar los archivos del proyecto al facilitar un modo de dividir las listas de elementos en diferentes lotes y pasar cada uno de ellos a una tarea por separado.  Esto significa que un archivo de proyecto sólo tiene que declarar una vez la tarea y sus atributos, aunque se pueda ejecutar varias veces.  
  
 Es posible especificar que se desea que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] realice el procesamiento por lotes con una tarea mediante la notación %\(*nombreDeMetadatosDeElemento*\) en uno de los atributos de la tarea.  En el ejemplo siguiente, se divide la lista de elementos `Example` en lotes basándose en el valor de los metadatos del elemento `Color`, y se pasa cada lote a la tarea `MyTask` por separado.  
  
> [!NOTE]
>  Si no se hace referencia a la lista de elementos en ninguna parte de los atributos de la tarea o si el nombre de los metadatos es ambiguo, se podrá usar la notación %\(*colecciónDeElementos.nombreDeMetadatosDeElemento*\) para que el valor de los metadatos de elementos tenga un nombre completo que se pueda utilizar en el procesamiento por lotes.  
  
```  
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
  
 Para obtener ejemplos sobre el procesamiento por lotes más concretos, vea [Metadatos de elementos en el procesamiento por lotes de tareas](../msbuild/item-metadata-in-task-batching.md).  
  
## Procesamiento por lotes de destinos  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] comprueba si las entradas y los resultados de un destino están actualizados antes de ejecutar el destino.  Si las entradas y los resultados están actualizados, se omite el destino.  Si una tarea incluida en un destino usa el procesamiento por lotes, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] debe determinar si las entradas y los resultados de cada lote de elementos están actualizados.  De lo contrario, el destino se ejecutará cada vez que se alcance.  
  
 En el ejemplo siguiente se muestra un elemento `Target` que contiene un atributo `Outputs` con la notación %\(*nombreDeMetadatosDeElemento*\).  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dividirá la lista de elementos `Example` en lotes basándose en los metadatos de elementos `Color` y analizará las marcas de tiempo de los archivos de salida para cada lote.  Si los resultados de un lote no están actualizados, se ejecutará el destino.  De lo contrario, se omitirá el destino.  
  
```  
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
  
 Para obtener otro ejemplo de procesamiento por lotes de destinos, vea [Metadatos de elementos en procesamiento por lotes de destinos](../msbuild/item-metadata-in-target-batching.md).  
  
## Funciones de propiedad con metadatos  
 El procesamiento por lotes se puede controlar mediante funciones de propiedad que incluyen metadatos.  Por ejemplo,  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 usa <xref:System.IO.Path.Combine%2A> para combinar una ruta de acceso a la carpeta raíz con una ruta de acceso al elemento Compile.  
  
 Las funciones de propiedad no pueden aparecer en los valores de los metadatos.  Por ejemplo,  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 no se permite.  
  
 Para obtener más información acerca de las funciones de propiedad, vea [Funciones de propiedad](../msbuild/property-functions.md).  
  
## Vea también  
 [Elemento ItemMetadata \(MSBuild\)](../msbuild/itemmetadata-element-msbuild.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)