---
title: Elemento ItemMetadata (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18e1722fcd6867ca5e8ae52e220ff0a3dd2a3b7f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633621"
---
# <a name="itemmetadata-element-msbuild"></a>Elemento ItemMetadata (MSBuild)

Contiene una clave de metadatos de elemento definida por el usuario que incluye el valor de metadatos del elemento. Un elemento puede tener cualquier número de pares clave-valor de metadatos.

 \<Project> \<ItemGroup> \<Item>

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
