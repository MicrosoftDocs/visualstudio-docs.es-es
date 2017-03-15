---
title: "Metadatos de elementos en procesamiento por lotes de destinos | Microsoft Docs"
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
  - "MSBuild, procesamiento por lotes de destino"
  - "procesamiento por lotes de destino [MSBuild]"
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Metadatos de elementos en procesamiento por lotes de destinos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] puede realizar análisis de dependencias de las entradas y los resultados de un destino de compilación.  Si se determina que las entradas o las salidas del destino están actualizadas, el destino se omite y la compilación continúa.  Los elementos `Target` utilizan los atributos `Inputs` y `Outputs` para especificar los elementos que se deben inspeccionar durante el análisis de dependencias.  
  
 Si un destino contiene una tarea que usa elementos procesados por lotes como entradas o resultados, el elemento `Target` del destino deberá utilizar el procesamiento por lotes en sus atributos `Inputs` o `Outputs` para permitir que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] omita los lotes de elementos que ya estén actualizados.  
  
## Procesar destinos por lotes  
 El ejemplo siguiente contiene una lista de elementos denominada `Res` que se divide en dos lotes basándose en los metadatos de los elementos `Culture`.  Cada uno de estos lotes se pasa a la tarea `AL`, que crea un ensamblado de salida para cada lote.  Mediante el procesamiento por lotes en el atributo `Outputs` del elemento `Target`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] puede determinar si cada lote individual está actualizado antes de ejecutar el destino.  Si no se utiliza el procesamiento por lotes de destinos, la tarea ejecuta ambos lotes de elementos cada vez que se ejecute el destino.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Res Include="Strings.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Strings.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.fr.resources">  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include="Dialogs.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
        <Res Include="Menus.jp.resources">  
            <Culture>jp</Culture>  
        </Res>  
    </ItemGroup>  
  
    <Target Name="Build"  
        Inputs="@(Res)"  
        Outputs="%(Culture)\MyApp.resources.dll">  
  
        <AL Resources="@(Res)"  
            TargetType="library"  
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## Vea también  
 [Cómo: Compilar versiones incrementalmente](../msbuild/how-to-build-incrementally.md)   
 [Procesamiento por lotes](../msbuild/msbuild-batching.md)   
 [Elemento Target \(MSBuild\)](../msbuild/target-element-msbuild.md)   
 [Metadatos de elementos en el procesamiento por lotes de tareas](../msbuild/item-metadata-in-task-batching.md)