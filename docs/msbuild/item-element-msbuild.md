---
title: Elemento Item (MSBuild) | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa el elemento Item para contener otro definido por el usuario y sus metadatos. Cada elemento debe ser un secundario de un elemento ItemGroup.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Item Element [MSBuild]
- <Item> Element [MSBuild]
ms.assetid: dcef5f91-0613-4bfc-8ee9-d7004bb6d3a9
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59a0660bb78e966150a6ef8d17dc24512a901a26
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913952"
---
# <a name="item-element-msbuild"></a>Elemento Item (MSBuild)

Contiene un elemento definido por el usuario y sus metadatos. Cada elemento que se utiliza en un proyecto de MSBuild debe especificarse como elemento secundario de un elemento `ItemGroup`.

\<Project>
\<ItemGroup>
\<Item>

## <a name="syntax"></a>Sintaxis

```xml
<Item Include="*.cs"
        Exclude="MyFile.cs"
        Condition="'String A'=='String B'">
    <ItemMetadata1>...</ItemMetadata1>
    <ItemMetadata2>...</ItemMetadata2>
</Item>
```

## <a name="specify-metadata-as-attributes"></a>Especificar metadatos como atributos

En MSBuild 15.1 o versiones posteriores, los metadatos con un nombre que no entre en conflicto con la lista actual de atributos pueden expresarse opcionalmente como un atributo.

Por ejemplo, para especificar una lista de paquetes NuGet, normalmente se usaría algo parecido a la sintaxis siguiente.

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json">
    <Version>9.0.1-beta1<Version>
  </PackageReference>
</ItemGroup>
```

Ahora, puede pasar los metadatos `Version` como un atributo, como se muestra en la sintaxis siguiente:

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1-beta1" />
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Include`|Atributo opcional.<br /><br /> El archivo o comodín que se incluirá en la lista de elementos.|
|`Exclude`|Atributo opcional.<br /><br /> El archivo o comodín que se excluirá de la lista de elementos.|
|`Condition`|Atributo opcional.<br /><br /> La condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|
|`Remove`|Atributo opcional.<br /><br /> El archivo o comodín que se quitará de la lista de elementos.<br /><br />|
|`KeepDuplicates`|Atributo opcional.<br /><br /> Especifica si se debe agregar al grupo de destino un elemento que es un duplicado exacto de un elemento existente. Si el elemento de origen y de destino tienen el mismo valor `Include` pero distintos metadatos, el elemento se agrega aunque `KeepDuplicates` está establecido en `false`. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).<br /><br /> Este atributo solo es válido si se ha especificado para un elemento de un `ItemGroup` que se encuentra en un `Target`.|
|`KeepMetadata`|Atributo opcional.<br /><br /> Los metadatos de los elementos de origen que se van a agregar a los elementos de destino. Solo los metadatos cuyos nombres están especificados en la lista delimitada por punto y coma se transfieren desde un elemento de origen a un elemento de destino. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).<br /><br /> Este atributo solo es válido si se ha especificado para un elemento de un `ItemGroup` que se encuentra en un `Target`.|
|`RemoveMetadata`|Atributo opcional.<br /><br /> Los metadatos de los elementos de origen que no se van a transferir a los elementos de destino. Todos los metadatos se transfieren desde un elemento de origen a un elemento de destino excepto aquellos cuyos nombres figuran en la lista de nombres delimitada por punto y coma. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).<br /><br /> Este atributo solo es válido si se ha especificado para un elemento de un `ItemGroup` que se encuentra en un `Target`.|
|`Update`|Atributo opcional. (Disponible únicamente para los proyectos de .NET Core en Visual Studio 2017 o versiones posteriores).<br /><br /> Permite modificar los metadatos de un elemento; normalmente se usa para invalidar los metadatos predeterminados de elementos concretos después de especificar inicialmente un grupo de elementos (por ejemplo, con un carácter comodín).<br /><br /> Este atributo solo es válido si se ha especificado para un elemento de un `ItemGroup` que no se encuentra en un `Target`.|

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

El empleo de la notación @(\<myType>) permite expandir una colección de elementos de tipo \<myType> en una lista de cadenas delimitada por puntos y coma, y pasarla a un parámetro. Si el parámetro es de tipo `string`, entonces el valor del parámetro es la lista de elementos separados por punto y coma. Si el parámetro es una matriz de cadenas (`string[]`), entonces cada elemento se inserta en la matriz según la ubicación de los signos punto y coma. Si el parámetro de tarea es de tipo <xref:Microsoft.Build.Framework.ITaskItem>`[]`, el valor es el contenido de la colección de elementos junto con los metadatos adjuntos. Para delimitar cada elemento mediante un carácter que no sea un punto y coma, use la sintaxis @(\<myType>, "\<separator>").

El motor de MSBuild puede evaluar comodines como `*` y `?`, y comodines recursivos como */\*\*/\*.cs*. Para obtener más información, consulte [Elementos](../msbuild/msbuild-items.md).

## <a name="examples"></a>Ejemplos

En el ejemplo de código siguiente se muestra la declaración de dos elementos de tipo `CSFile`. El segundo elemento declarado contiene metadatos en los que `MyMetadata` está establecido en `HelloWorld`.

```xml
<ItemGroup>
    <CSFile Include="engine.cs; form.cs" />
    <CSFile Include="main.cs" >
        <MyMetadata>HelloWorld</MyMetadata>
    </CSFile>
</ItemGroup>
```

En el ejemplo de código siguiente se muestra cómo usar el atributo `Update` para modificar los metadatos de un archivo denominado *somefile.cs* que se ha incluido mediante un glob. (Disponible únicamente para los proyectos de .NET Core en Visual Studio 2017 o versiones posteriores).

```xml
<ItemGroup>
    <Compile Update="somefile.cs">  // or Update="*.designer.cs"
        <MetadataKey>MetadataValue</MetadataKey>
    </Compile>
</ItemGroup>
```

## <a name="see-also"></a>Vea también

- [Elementos](../msbuild/msbuild-items.md)
- [Elementos comunes de proyectos de MSBuild](../msbuild/common-msbuild-project-items.md)
- [Propiedades de MSBuild](../msbuild/msbuild-properties.md)
- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
