---
title: Elemento Property (MSBuild) | Microsoft Docs
description: Obtenga información sobre el elemento Property de MSBuild, que contiene un nombre de propiedad definido por el usuario y un valor que se debe especificar como elemento secundario de un elemento PropertyGroup.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 617a6d3712b137d76334d4063f36a1b8dde1d101
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918856"
---
# <a name="property-element-msbuild"></a>Elemento Property (MSBuild)

Contiene un valor y un nombre de propiedad definidos por el usuario. Cada propiedad que se utiliza en un proyecto de MSBuild debe especificarse como elemento secundario de un elemento `PropertyGroup`.

 \<Project> \<PropertyGroup>

## <a name="syntax"></a>Sintaxis

```xml
<Property Condition="'String A' == 'String B'">
    Property Value
</Property>
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
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento de agrupamiento de las propiedades.|

## <a name="text-value"></a>Valor de texto

 El valor de texto es opcional.

 Este texto especifica el valor de propiedad y puede contener XML.

## <a name="remarks"></a>Comentarios

 Los nombres de propiedad se limitan únicamente a caracteres ASCII. En el proyecto, se hace referencia a los valores de propiedad colocando el nombre de propiedad entre "`$(`" y "`)`". Por ejemplo, `$(builddir)\classes` se resolvería como *build\classes* si la propiedad `builddir` tuviera el valor `build`. Para más información sobre las propiedades, consulte [Propiedades de MSBuild](../msbuild/msbuild-properties.md).

## <a name="example"></a>Ejemplo

 El código siguiente establece la propiedad `Optimization` en `false` y la propiedad `DefaultVersion` en `1.0` si la propiedad `Version` está vacía.

```xml
<PropertyGroup>
    <Optimization>false</Optimization>
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>
</PropertyGroup>
```

## <a name="see-also"></a>Vea también

- [Propiedades de MSBuild](../msbuild/msbuild-properties.md)
- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
