---
title: Elemento Item (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dfec558a9958d980d25d4160c4b7f2ce269cbb5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270042"
---
# <a name="item-element-msbuild"></a>Elemento Item (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Contiene un elemento definido por el usuario y sus metadatos. Cada elemento que se utiliza en un proyecto de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] debe especificarse como elemento secundario de un elemento `ItemGroup`.  
  
 \<Project>  
 \<ItemGroup>  
 \<Item>  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<Item Include="*.cs"  
        Exclude="MyFile.cs"  
        Remove="RemoveFile.cs"  
        Condition="'String A'=='String B'" >  
    <ItemMetadata1>...</ItemMetadata1>  
    <ItemMetadata2>...</ItemMetadata2>  
</Item>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Include`|Atributo necesario.<br /><br /> El archivo o comodín que se incluirá en la lista de elementos.|  
|`Exclude`|Atributo opcional.<br /><br /> El archivo o comodín que se excluirá de la lista de elementos.|  
|`Condition`|Atributo opcional.<br /><br /> La condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|  
|`Remove`|Atributo opcional.<br /><br /> El archivo o comodín que se quitará de la lista de elementos.<br /><br /> Este atributo solo es válido si se ha especificado para un elemento de un `ItemGroup` que se encuentra en un `Target`.|  
|`KeepMetadata`|Atributo opcional.<br /><br /> Los metadatos de los elementos de origen que se van a agregar a los elementos de destino. Solo los metadatos cuyos nombres están especificados en la lista delimitada por punto y coma se transfieren desde un elemento de origen a un elemento de destino. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).<br /><br /> Este atributo solo es válido si se ha especificado para un elemento de un `ItemGroup` que se encuentra en un `Target`.|  
|`RemoveMetadata`|Atributo opcional.<br /><br /> Los metadatos de los elementos de origen que no se van a transferir a los elementos de destino. Todos los metadatos se transfieren desde un elemento de origen a un elemento de destino excepto aquellos cuyos nombres figuran en la lista de nombres delimitada por punto y coma. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).<br /><br /> Este atributo solo es válido si se ha especificado para un elemento de un `ItemGroup` que se encuentra en un `Target`.|  
|`KeepDuplicates`|Atributo opcional.<br /><br /> Especifica si se debe agregar al grupo de destino un elemento que es un duplicado exacto de un elemento existente. Si el elemento de origen y de destino tienen el mismo valor `Include` pero distintos metadatos, el elemento se agrega aunque `KeepDuplicates` está establecido en `false`. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).<br /><br /> Este atributo solo es válido si se ha especificado para un elemento de un `ItemGroup` que se encuentra en un `Target`.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)|Una clave de metadatos de elemento definida por el usuario que contiene el valor de metadatos del elemento. Puede haber cero o más elementos `ItemMetadata` en un elemento.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento grouping de los elementos.|  
  
## <a name="remarks"></a>Comentarios  
 Los elementos `Item` definen las entradas en el sistema de compilación y se agrupan en colecciones de elementos basadas en sus nombres de colección definidos por el usuario. Estas colecciones de elementos se pueden utilizar como parámetros para las [tareas](../msbuild/msbuild-tasks.md), que utilizan los elementos individuales de las colecciones para llevar a cabo los pasos del proceso de compilación. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).  
  
 Al utilizar la notación `@(`*myType*`)`, una colección de elementos de tipo *myType* se puede expandir en una lista de cadenas delimitada por punto y coma y pasar a un parámetro. Si el parámetro es de tipo `string`, entonces el valor del parámetro es la lista de elementos separados por punto y coma. Si el parámetro es una matriz de cadenas (`string[]`), entonces cada elemento se inserta en la matriz según la ubicación de los signos punto y coma. Si el parámetro de tarea es de tipo <xref:Microsoft.Build.Framework.ITaskItem>`[]`, el valor es el contenido de la colección de elementos junto con los metadatos adjuntos. Para delimitar cada elemento mediante un carácter que no sea un punto y coma, utilice la sintaxis `@(`*myType*`, '`*separator*`')`.  
  
 El motor de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] puede evaluar comodines como `*` y `?`, y comodines recursivos como `/**/*.cs`. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra la declaración de dos elementos de tipo `CSFile`. El segundo elemento declarado contiene metadatos en los que `MyMetadata` está establecido en `HelloWorld`.  
  
```  
<ItemGroup>  
    <CSFile Include="engine.cs; form.cs" />  
    <CSFile Include="main.cs" >  
        <MyMetadata>HelloWorld</MyMetadata>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Vea también  
 [Elementos](../msbuild/msbuild-items.md)   
 [Propiedades de MSBuild](msbuild-properties1.md)   
 [Referencia de esquemas de archivo del proyecto](../msbuild/msbuild-project-file-schema-reference.md)



