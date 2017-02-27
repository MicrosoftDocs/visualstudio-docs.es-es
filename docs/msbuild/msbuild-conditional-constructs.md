---
title: "Construcciones condicionales de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Choose> (elemento) [MSBuild]"
  - "<Otherwise> (elemento) [MSBuild]"
  - "<When> (elemento) [MSBuild]"
  - "Choose (elemento) [MSBuild]"
  - "construcciones condicional [MSBuild]"
  - "MSBuild, construcciones condicionales"
  - "Otherwise (elemento) [MSBuild]"
  - "When (elemento) [MSBuild]"
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Construcciones condicionales de MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proporciona un mecanismo para un posible procesamiento con los elementos [Choose](../msbuild/choose-element-msbuild.md), [When](../msbuild/when-element-msbuild.md) y [Otherwise](../msbuild/otherwise-element-msbuild.md).  
  
## Utilización del elemento Choose  
 El elemento `Choose` contiene una serie de elementos `When` con atributos `Condition` que se comprueban de forma ordenada de arriba abajo hasta que uno aparece evaluado como `true`.  Si más de un elemento `When` resulta evaluado como `true`, sólo se utilizará el primero.  Se evaluará un elemento `Otherwise`, en caso de encontrarse presente, si ninguna condición en un elemento `When` resulta evaluada como `true`.  
  
 Los elementos `Choose` se pueden utilizar como elementos secundarios de elementos `Project`, `When` y `Otherwise`.  Los elementos `When` y `Otherwise` pueden tener elementos secundarios `ItemGroup`, `PropertyGroup` o `Choose`.  
  
## Ejemplo  
 En el ejemplo siguiente se utilizan los elementos `Choose` y `When` para cualquier posible procesamiento.  Las propiedades y los elementos para el proyecto se establecen dependiendo del valor de la propiedad `Configuration`.  
  
```  
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
  
## Vea también  
 [Elemento Choose \(MSBuild\)](../msbuild/choose-element-msbuild.md)   
 [Elemento When \(MSBuild\)](../msbuild/when-element-msbuild.md)   
 [Elemento Otherwise \(MSBuild\)](../msbuild/otherwise-element-msbuild.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)