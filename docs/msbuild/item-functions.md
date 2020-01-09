---
title: Funciones de elementos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65ca003375e54248852f5942bd2b5f62fe21a06c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573799"
---
# <a name="item-functions"></a>funciones de elementos
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

|Función|Ejemplo|Descripción|
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
- [Elementos](../msbuild/msbuild-items.md)
