---
title: Elemento ItemMetadata (MSBuild) | Microsoft Docs
description: Obtenga información sobre el elemento ItemMetadata de MSBuild, que contiene una clave de metadatos de elementos definida por el usuario que tiene el valor de los metadatos.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f48c57769ff6f969e68a50418b017d9928149fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913824"
---
# <a name="itemmetadata-element-msbuild"></a>Elemento ItemMetadata (MSBuild)

Contiene una clave de metadatos de elemento definida por el usuario que incluye el valor de metadatos del elemento. Un elemento puede tener cualquier número de pares clave-valor de metadatos.

 \<Project> \<ItemGroup>
 \<Item>

## <a name="syntax"></a>Sintaxis

```xml
<ItemMetadataName> Item Metadata value</ItemMetadataName>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Condition`|Atributo opcional.<br /><br /> Condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementos secundarios

 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Un elemento definido por el usuario que define las entradas para el proceso de compilación.|

## <a name="text-value"></a>Valor de texto

 El valor de texto es opcional.

 Este texto especifica el valor de metadatos del elemento, que puede ser texto o XML.

## <a name="example"></a>Ejemplo

 En el ejemplo de código siguiente se muestra cómo agregar los metadatos `Culture` con el valor `fr` al elemento `CSFile`.

```xml
<ItemGroup>
    <CSFile Include="main.cs" >
        <Culture>fr</Culture>
    </CSFile>
</ItemGroup>
```

## <a name="see-also"></a>Vea también

- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementos](../msbuild/msbuild-items.md)
