---
title: "Funciones de elementos | Microsoft Docs"
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
  - "msbuild, funciones de elementos"
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
caps.latest.revision: 28
caps.handback.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Funciones de elementos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A partir de MSBuild 4.0, el código de las tareas y los destinos pueden llamar a funciones de elementos para obtener información sobre los elementos del proyecto.  Estas funciones simplifican la obtención de elementos Distinct\(\) y son más rápidas que si se recorren en bucle los elementos.  
  
## Funciones del elemento de cadena  
 Puede utilizar los métodos y propiedades de cadena en .NET Framework para trabajar con cualquier valor del elemento.  Para los métodos <xref:System.String> , especifique el nombre del método.  Para las propiedades <xref:System.String> , especifique el nombre de propiedad después de “get\_”.  
  
 Para los elementos que tienen varias cadenas, el método de la cadena o ejecuta la propiedad en cada cadena.  
  
 El ejemplo siguiente se muestra cómo utilizar estas funciones de elementos de la cadena.  
  
```  
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
  
## Funciones intrínsecas de elemento  
 En la tabla siguiente se muestran las funciones intrínsecas disponibles para los elementos.  
  
|Función|Ejemplo|Descripción|  
|-------------|-------------|-----------------|  
|`Count`|`@(MyItem->Count())`|Devuelve el número de elementos.|  
|`DirectoryName`|`@(MyItem->DirectoryName())`|Devuelve el equivalente `Path.DirectoryName` para cada elemento.|  
|`Distinct`|`@(MyItem->Distinct())`|Devuelve los elementos que tienen valores distintos `Include` .  Se omiten los metadatos.  En la comparación no se distingue entre mayúsculas y minúsculas.|  
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|Devuelve los elementos que tienen valores distintos `itemspec` .  Se omiten los metadatos.  En la comparación se distingue entre mayúsculas y minúsculas.|  
|`Reverse`|`@(MyItem->Reverse())`|Devuelve los elementos en orden inverso.|  
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|Devuelve `boolean` para indicar si cualquier elemento tiene los metadatos con nombre y valor.  En la comparación no se distingue entre mayúsculas y minúsculas.|  
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|Devuelve los elementos con sus metadatos borrados.  Sólo se conserva `itemspec` .|  
|`HasMetadata`|`@(MyItem->HasMetadataValue("MetadataName")`|Devuelve los elementos que tienen el nombre especificado de metadatos.  En la comparación no se distingue entre mayúsculas y minúsculas.|  
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|Devuelve los valores de metadatos que tiene el nombre de los metadatos.|  
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue")`|Devuelve los elementos que tienen los metadatos con nombre y valor.  En la comparación no se distingue entre mayúsculas y minúsculas.|  
  
 El ejemplo siguiente se muestra cómo utilizar funciones intrínsecas del elemento.  
  
```  
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
  
## Vea también  
 [elementos](../msbuild/msbuild-items.md)