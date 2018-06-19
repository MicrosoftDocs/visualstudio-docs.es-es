---
title: Funciones de elementos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93c8a16b1ab15354deafc236d9f4845b051d58f7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31572809"
---
# <a name="item-functions"></a>Funciones de elementos
A partir de MSBuild 4.0, el código de las tareas y de los destinos puede llamar a funciones de elementos para obtener información sobre los elementos del proyecto. Estas funciones simplifican la obtención de elementos Distinct() y son más rápidas que si se recorren en bucle los elementos.  
  
## <a name="string-item-functions"></a>Funciones de elementos de cadena  
 Puede usar métodos y propiedades de cadena en .NET Framework para operar en cualquier valor del elemento. Para los métodos <xref:System.String>, especifique el nombre del método. Para las propiedades <xref:System.String>, especifique el nombre de la propiedad después de "get_".  
  
 Para los elementos que tienen varias cadenas, el método o la propiedad de cadena se ejecuta en cada cadena.  
  
 En el ejemplo siguiente, se muestra cómo utilizar estas funciones de elementos de cadena.  
  
```xml  
<ItemGroup>  
    <theItem Include="andromeda;tadpole;cartwheel" />  
</ItemGroup>  
  
<Target Name = "go">  
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />  
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />  
    <Message Text="Length   @(theItem->get_Length())" />  
    <Message Text="Chars    @(theItem->get_Chars(2))" />  
</Target>  
  
  <!--  
  Output:  
    IndexOf  3;-1;2  
    Replace  andromeda;pinwheel;cartwheel  
    Length   9;7;9  
    Chars    d;d;r  
  -->  
```  
  
## <a name="intrinsic-item-functions"></a>Funciones de elementos intrínsecas  
 En la tabla siguiente se enumeran las funciones intrínsecas disponibles para los elementos.  
  
|Función|Ejemplo|Description|  
|--------------|-------------|-----------------|  
|`Count`|`@(MyItem->Count())`|Devuelve el número de elementos.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|Devuelve el equivalente de `Path.DirectoryName` para cada elemento.|  
|`Distinct`|`@(MyItem->Distinct())`|Devuelve elementos que tienen valores `Include` distintos. Los metadatos se omiten. En la comparación no se distingue entre mayúsculas y minúsculas.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Devuelve elementos que tienen valores `itemspec` distintos. Los metadatos se omiten. En la comparación se distingue entre mayúsculas y minúsculas.|  
|`Reverse`|`@(MyItem->Reverse())`|Devuelve los elementos en orden inverso.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Devuelve un `boolean` para indicar si un elemento tiene el nombre y el valor de los metadatos especificados. En la comparación no se distingue entre mayúsculas y minúsculas.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Devuelve elementos en los que se han borrado los metadatos. Solo se retiene el `itemspec`.|  
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|Devuelve elementos que tienen el nombre de los metadatos especificado. En la comparación no se distingue entre mayúsculas y minúsculas.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Devuelve los valores de los metadatos que tienen el nombre de los metadatos.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|Devuelve elementos que tienen el nombre y el valor de los metadatos especificados. En la comparación no se distingue entre mayúsculas y minúsculas.|  
  
 En el ejemplo siguiente, se muestra cómo utilizar las funciones de elementos intrínsecas.  
  
```xml  
<ItemGroup>  
    <TheItem Include="first">  
        <Plant>geranium</Plant>  
    </TheItem>  
    <TheItem Include="second">  
        <Plant>algae</Plant>  
    </TheItem>  
    <TheItem Include="third">  
        <Plant>geranium</Plant>  
    </TheItem>  
</ItemGroup>  
  
<Target Name="go">  
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />  
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />  
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />  
    <Message Text=" " />  
    <Message Text="Count:   @(theItem->Count())" />  
    <Message Text="Reverse: @(theItem->Reverse())" />  
</Target>  
  
  <!--   
  Output:  
    MetaData:    geranium;algae;geranium  
    HasMetadata: first;second;third  
    WithMetadataValue: first;third  
  
    Count:   3  
    Reverse: third;second;first  
  -->  
```  
  
## <a name="see-also"></a>Vea también  
 [Elementos](../msbuild/msbuild-items.md)
