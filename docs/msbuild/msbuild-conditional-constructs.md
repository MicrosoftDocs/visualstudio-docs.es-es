---
title: Construcciones condicionales de MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26891fa67616b1796499722e03a764da2a8fd7d6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589271"
---
# <a name="msbuild-conditional-constructs"></a>Construcciones condicionales de MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proporciona un mecanismo para cualquier procesamiento con los elementos [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) y [Otherwise](../msbuild/otherwise-element-msbuild.md).

## <a name="use-the-choose-element"></a>Usar el elemento Choose
 El elemento `Choose` contiene una serie de elementos `When` con atributos `Condition` que se prueban en orden de arriba abajo, hasta que uno se evalúe como `true`. Si más de un elemento `When` se evalúa como `true`, se usará solo el primero. Se evaluará un elemento `Otherwise`, en caso de estar presente, si ninguna condición de un elemento `When` se evalúa como `true`.

 Los elementos `Choose` se pueden usar como elementos secundarios de los elementos `Project`, `When` y `Otherwise`. Los elementos `When` y `Otherwise` pueden tener elementos secundarios `ItemGroup`, `PropertyGroup` o `Choose`.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se usan los elementos `Choose` y `When` para cualquier procesamiento. Las propiedades y los elementos del proyecto se establecen en función dl valor de la propiedad `Configuration`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='Debug' ">
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
    </Choose>
    <!-- Rest of Project -->
</Project>
```

## <a name="see-also"></a>Vea también
- [Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)
- [Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)
- [Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
