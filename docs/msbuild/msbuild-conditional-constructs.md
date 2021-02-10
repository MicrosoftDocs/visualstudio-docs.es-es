---
title: Construcciones condicionales de MSBuild | Microsoft Docs
description: Obtenga información sobre cómo MSBuild proporciona un mecanismo para el procesamiento condicional con los elementos Choose, When y Otherwise.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10b26e9bdc0c632f924a29cd2ad09c21f8048d31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919137"
---
# <a name="msbuild-conditional-constructs"></a>Construcciones condicionales de MSBuild

MSBuild proporciona un mecanismo para cualquier procesamiento con los elementos [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) y [Otherwise](../msbuild/otherwise-element-msbuild.md).

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

En este ejemplo, se utiliza una condición en una constante del compilador `DEFINED_CONSTANT`. Éstas se incluyen en la propiedad `DefinedConstants`. La expresión regular se usa para hacer coincidir la constante exacta en una lista separada por punto y coma.

```xml
<Choose>
   <When Condition="$([System.Text.RegularExpressions.Regex]::IsMatch(
         $(DefineConstants), '^(.*;)*DEFINED_CONSTANT(;.*)*$'))">
      <!-- When DEFINED_CONSTANT is defined. -->
   </When>
   <!-- other conditions -->
</Choose>
```

## <a name="see-also"></a>Vea también

- [Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)
- [Elemento When (MSBuild)](../msbuild/when-element-msbuild.md)
- [Elemento Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
