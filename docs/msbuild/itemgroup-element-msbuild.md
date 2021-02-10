---
title: Elemento ItemGroup (MSBuild) | Microsoft Docs
description: Obtenga información sobre el elemento ItemGroup de MSBuild, que contiene un conjunto de elementos Item definidos por el usuario. Cada elemento debe ser un secundario de un elemento ItemGroup.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eff27467aeea5068f3ec086b490ca9c735861549
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913850"
---
# <a name="itemgroup-element-msbuild"></a>Elemento ItemGroup (MSBuild)

Contiene un conjunto de elementos [Item](../msbuild/item-element-msbuild.md) definidos por el usuario. Cada elemento que se utiliza en un proyecto de MSBuild debe especificarse como elemento secundario de un elemento `ItemGroup`.

\<Project>
\<ItemGroup>

## <a name="syntax"></a>Sintaxis

```xml
<ItemGroup Condition="'String A' == 'String B'"
           Label="Label">
    <Item1>... </Item1>
    <Item2>... </Item2>
</ItemGroup>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Condition`|Atributo opcional. Condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|
|`Label`|Atributo opcional. Identifica la `ItemGroup`. |

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Item](../msbuild/item-element-msbuild.md)|Define las entradas para el proceso de compilación. Puede haber cero o más elementos `Item` en un `ItemGroup`.|

### <a name="parent-elements"></a>Elementos primarios

| Elemento | Descripción |
| - | - |
| [Proyecto](../msbuild/project-element-msbuild.md) | Elemento raíz necesario de un archivo de proyecto de MSBuild. |
| [Target](../msbuild/target-element-msbuild.md) | A partir de .NET Framework 3.5, el elemento `ItemGroup` puede aparecer dentro de un elemento `Target`. Para obtener más información, consulte [Destinos](../msbuild/msbuild-targets.md). |

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestran las colecciones de elementos definidos por el usuario `Res` y `CodeFiles` declaradas dentro de un elemento `ItemGroup`. Cada uno de los elementos de la colección de elementos `Res` contiene un elemento secundario [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) definido por el usuario.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Res Include = "Strings.fr.resources" >
            <Culture>fr</Culture>
        </Res>
        <Res Include = "Dialogs.fr.resources" >
            <Culture>fr</Culture>
        </Res>

        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />
        <CodeFiles Include="..\..\Resources\Constants.cs" />
    </ItemGroup>
...
</Project>
```

En un archivo de proyecto simple, normalmente se usa un solo elemento `ItemGroup`, pero también se pueden utilizar varios elementos `ItemGroup`. Cuando se utilizan varios elementos `ItemGroup`, los elementos se combinan en un solo `ItemGroup`. Por ejemplo, algunos elementos podrían estar incluidos en un elemento `ItemGroup` independiente que se define en un archivo importado.

Pueden aplicarse condiciones a los elementos ItemGroup mediante el atributo `Condition`. En ese caso, los elementos solo se agregan a la lista de elementos si se cumple la condición. Consulte [Condiciones de MSBuild](msbuild-conditions.md).

El atributo `Label` se utiliza en algunos sistemas de compilación como una manera de controlar los comportamientos de la compilación. Solo se puede usar en declaraciones, como una manera de crear scripts de MSBuild más comprensibles o como una configuración de control para que afecte a las acciones de compilación.

## <a name="see-also"></a>Vea también

- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementos](../msbuild/msbuild-items.md)
- [Elementos comunes de proyectos de MSBuild](../msbuild/common-msbuild-project-items.md)
