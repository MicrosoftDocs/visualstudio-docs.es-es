---
title: Metadatos de elementos en el procesamiento por lotes de destinos | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2d91e294165012bea3b1ac196011cf9908469a7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566951"
---
# <a name="item-metadata-in-target-batching"></a>Metadatos de elementos en procesamiento por lotes de destinos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [metadatos de elementos en procesamiento por lotes de destino](https://docs.microsoft.com/visualstudio/msbuild/item-metadata-in-target-batching).  
  
  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] puede realizar el análisis de dependencias de las entradas y las salidas de un destino de compilación. Si se determina que las entradas o las salidas del destino están actualizadas, el destino se omite y la compilación continúa. Los elementos `Target` usan los atributos `Inputs` y `Outputs` para especificar los elementos que se van a inspeccionar durante el análisis de dependencias.  
  
 Si un destino contiene una tarea que usa elementos procesados por lotes como entradas o salidas, el elemento `Target` del destino debe usar el procesamiento por lotes en sus atributos `Inputs` o `Outputs` para permitir que [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] omita los lotes de elementos que ya están actualizados.  
  
## <a name="batching-targets"></a>Procesamiento por lotes de destinos  
 El ejemplo siguiente contiene una lista de elementos denominada `Res` que se divide en dos lotes en función de los metadatos del elemento `Culture`. Cada uno de estos lotes se pasa a la tarea `AL`, que crea un ensamblado de salida para cada lote. Mediante el uso del procesamiento por lotes en el atributo `Outputs` del elemento `Target`, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] puede determinar si cada lote individual está actualizado antes de ejecutar el destino. Si no se usara el procesamiento por lotes de destinos, la tarea ejecutaría ambos lotes de elementos cada vez que se ejecutara el destino.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Cómo: Compilar versiones incrementalmente](../msbuild/how-to-build-incrementally.md)   
 [Procesamiento por lotes](../msbuild/msbuild-batching.md)   
 [Elemento Target (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Metadatos de elementos en el procesamiento por lotes de tareas](../msbuild/item-metadata-in-task-batching.md)



