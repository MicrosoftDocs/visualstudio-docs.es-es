---
title: Procesamiento por lotes de MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d96330c01ab340d4db67694f358717a2dae0bce3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842655"
---
# <a name="msbuild-batching"></a>Procesamiento por lotes de MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] tiene la capacidad de dividir las listas de elementos en distintas categorías, o lotes, basándose en los metadatos de estos elementos, y luego ejecutar un destino o una tarea una vez con cada lote.  
  
## <a name="task-batching"></a>Procesamiento por lotes de tareas  
 El procesamiento por lotes de tareas le permite simplificar los archivos del proyecto porque proporciona una manera de dividir las listas de elementos en lotes diferentes y pasar cada uno de estos lotes a una tarea por separado. Esto significa que un archivo de proyecto solo necesita que la tarea y sus atributos se declaren una vez, aunque se puede ejecutar varias veces.  
  
 Especifique que desea [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] realizar el procesamiento por lotes con una tarea mediante la notación%(*ItemMetaDataName*) en uno de los atributos de la tarea. En el ejemplo siguiente, la lista de elementos `Example` se divide en lotes de acuerdo con el valor de los metadatos del elemento `Color` y pasa cada uno de los lotes a la tarea `MyTask` por separado.  
  
> [!NOTE]
> Si no hace referencia a la lista de elementos en ningún otro lugar de los atributos de la tarea, o si el nombre de los metadatos puede ser ambiguo, puede usar la notación%(*ItemCollection. ItemMetaDataName*) para completar el valor de los metadatos del elemento que se usará para el procesamiento por lotes.  
  
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
  
 Para obtener ejemplos más específicos de procesamiento por lotes, consulte [metadatos de elementos en procesamiento por lotes de tareas](../msbuild/item-metadata-in-task-batching.md).  
  
## <a name="target-batching"></a>Procesamiento por lotes de destinos  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] verifica si las entradas y las salidas de un destino están actualizadas antes de ejecutar el destino. Si las entradas y salidas están actualizadas, el destino se omite. Si una tarea dentro de un destino usa el procesamiento por lotes, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] debe determinar si las entradas y las salidas de cada lote de elementos están actualizadas. En caso contrario, el destino se ejecuta cada vez que se le llama.  
  
 En el ejemplo siguiente se muestra un `Target` elemento que contiene un `Outputs` atributo con la notación%(*ItemMetaDataName*). [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] dividirá la lista de elementos `Example` en lotes de acuerdo con los metadatos del elemento `Color` y analizará las marcas de tiempo de los archivos de salida para cada lote. Si las salidas de un lote no están actualizadas, se ejecuta el destino. En caso contrario, se omite el destino.  
  
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
  
 Para obtener otro ejemplo de procesamiento por lotes de destino, consulte [metadatos de elementos en procesamiento por lotes de destino](../msbuild/item-metadata-in-target-batching.md).  
  
## <a name="property-functions-using-metadata"></a>Funciones de propiedad que utilizan metadatos  
 El procesamiento por lotes puede controlarse mediante funciones de propiedad que incluyen metadatos. Por ejemplo,  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 utiliza <xref:System.IO.Path.Combine%2A> para combinar una ruta de acceso de directorio raíz con una ruta de acceso de elemento de compilación.  
  
 Es posible que las funciones de propiedad no aparezcan en los valores de los metadatos.  Por ejemplo,  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 no se permite.  
  
 Para obtener más información sobre las funciones de propiedad, consulte [funciones de propiedad](../msbuild/property-functions.md).  
  
## <a name="see-also"></a>Consulte también  
 [Elemento ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Conceptos de MSBuild](../msbuild/msbuild-concepts.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)
