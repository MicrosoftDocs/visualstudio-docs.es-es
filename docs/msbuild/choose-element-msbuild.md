---
title: Elemento Choose (MSBuild) | Microsoft Docs
description: Use el elemento Choose de MSBuild para evaluar los elementos secundarios y seleccione un conjunto de elementos ItemGroup o PropertyGroup para evaluar.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a3cb3ae9ef120954bb3c299cdf310a32da69845
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939518"
---
# <a name="choose-element-msbuild"></a>Elemento Choose (MSBuild)

Evalúa los elementos secundarios para seleccionar un conjunto de elementos `ItemGroup` o `PropertyGroup` para evaluar.

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Sintaxis

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Otherwise](../msbuild/otherwise-element-msbuild.md)|Elemento opcional.<br /><br /> Especifica el bloque de código `PropertyGroup` y los elementos `ItemGroup` que se evaluarán si las condiciones de todos los elementos `When` se evalúan como `false`. Puede haber un elemento `Otherwise` o ninguno en un elemento `Choose` y debe ser el último elemento.|
|[When](../msbuild/when-element-msbuild.md)|Elemento necesario.<br /><br /> Especifica un posible bloque de código que el elemento `Choose` puede seleccionar. Puede haber uno o más elementos `When` en un elemento `Choose`.|

### <a name="parent-elements"></a>Elementos primarios

| Elemento | Descripción |
| - | - |
| [Otherwise](../msbuild/otherwise-element-msbuild.md) | Especifica el bloque de código que se ejecutará si las condiciones de todos los elementos `When` se evalúan como `false`. |
| [Proyecto](../msbuild/project-element-msbuild.md) | Elemento raíz necesario de un archivo de proyecto de MSBuild. |
| [When](../msbuild/when-element-msbuild.md) | Especifica un posible bloque de código que el elemento `Choose` puede seleccionar. |

## <a name="remarks"></a>Observaciones

 Los elementos `Choose`, `When` y `Otherwise` se utilizan juntos para ofrecer un modo de seleccionar una sección de código para que ejecute una serie de alternativas posibles. Para obtener más información, vea [Construcciones condicionales](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Ejemplo

 En el proyecto siguiente se utiliza el elemento `Choose` para seleccionar el conjunto de valores de propiedad de los elementos `When` que desea establecer. Si los atributos `Condition` de ambos elementos `When` se evalúan como `false`, se establecen los valores de propiedad del elemento `Otherwise`.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='debug' ">
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <DebugType>full</DebugType>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\Debug\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
            <ItemGroup>
                <Compile Include="UnitTesting\*.cs" />
                <Reference Include="NUnit.dll" />
            </ItemGroup>
        </When>
        <When Condition=" '$(Configuration)'=='retail' ">
            <PropertyGroup>
                <DebugSymbols>false</DebugSymbols>
                <Optimize>true</Optimize>
                <OutputPath>.\bin\Release\</OutputPath>
                <DefineConstants>TRACE</DefineConstants>
            </PropertyGroup>
        </When>
        <Otherwise>
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\$(Configuration)\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
        </Otherwise>
    </Choose>
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="see-also"></a>Consulte también

- [Construcciones condicionales](../msbuild/msbuild-conditional-constructs.md)
- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
