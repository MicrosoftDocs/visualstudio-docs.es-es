---
title: Metadatos de elementos en el procesamiento por lotes de destinos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 486169788ad4533f5d45bf48c979ce3d0f5f7920
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081064"
---
# <a name="item-metadata-in-target-batching"></a>Metadatos de elementos en el procesamiento por lotes de destinos
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] puede realizar el análisis de dependencias de las entradas y las salidas de un destino de compilación. Si se determina que las entradas o las salidas del destino están actualizadas, el destino se omite y la compilación continúa. Los elementos `Target` usan los atributos `Inputs` y `Outputs` para especificar los elementos que se van a inspeccionar durante el análisis de dependencias.  
  
 Si un destino contiene una tarea que usa elementos procesados por lotes como entradas o salidas, el elemento `Target` del destino debe usar el procesamiento por lotes en sus atributos `Inputs` o `Outputs` para permitir que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] omita los lotes de elementos que ya están actualizados.  
  
## <a name="batch-targets"></a>Destinos de lotes  
 El ejemplo siguiente contiene una lista de elementos denominada `Res` que se divide en dos lotes en función de los metadatos del elemento `Culture`. Cada uno de estos lotes se pasa a la tarea `AL`, que crea un ensamblado de salida para cada lote. Mediante el uso del procesamiento por lotes en el atributo `Outputs` del elemento `Target`, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] puede determinar si cada lote individual está actualizado antes de ejecutar el destino. Si no se usara el procesamiento por lotes de destinos, la tarea ejecutaría ambos lotes de elementos cada vez que se ejecutara el destino.  
  
```xml  
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
  
## <a name="see-also"></a>Vea también  
 [Cómo: Compilar versiones incrementalmente](../msbuild/how-to-build-incrementally.md)   
 [Procesamiento por lotes](../msbuild/msbuild-batching.md)   
 [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Metadatos de elementos en el procesamiento por lotes de tareas](../msbuild/item-metadata-in-task-batching.md)