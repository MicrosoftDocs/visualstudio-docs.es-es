---
title: Elemento Otherwise (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 26c561c259641ce7bed118d8e4aa71c383b29b67
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327016"
---
# <a name="otherwise-element-msbuild"></a>Elemento Otherwise (MSBuild)
Especifica el bloque de código que se ejecutará solo si las condiciones de todos los elementos `When` se evalúan como `false`.  

 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  

## <a name="syntax"></a>Sintaxis  

```xml  
<Otherwise>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</Otherwise>  
```  

## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  

### <a name="attributes"></a>Atributos  
 Ninguno.  

### <a name="child-elements"></a>Elementos secundarios  

|Elemento|Descripción|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Elemento opcional.<br /><br /> Evalúa los elementos secundarios para seleccionar una sección de código y ejecutarla. Puede haber cero o más elementos `Choose` en un elemento `Otherwise`.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento opcional.<br /><br /> Contiene un conjunto de elementos [Item](../msbuild/item-element-msbuild.md) definidos por el usuario. Puede haber cero o más elementos `ItemGroup` en un elemento `Otherwise`.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento opcional.<br /><br /> Contiene un conjunto de elementos [Property](../msbuild/property-element-msbuild.md) definidos por el usuario. Puede haber cero o más elementos `PropertyGroup` en un elemento `Otherwise`.|  

### <a name="parent-elements"></a>Elementos primarios  

|Elemento|Descripción|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Evalúa los elementos secundarios para seleccionar una sección de código y ejecutarla.|  

## <a name="remarks"></a>Comentarios  
 Puede haber solo un elemento `Otherwise` en un elemento `Choose` y debe ser el último elemento.  

 Los elementos `Choose`, `When` y `Otherwise` se utilizan juntos para ofrecer un modo de seleccionar una sección de código para que ejecute una serie de alternativas posibles. Para obtener más información, consulte la sección [Construcciones condicionales](../msbuild/msbuild-conditional-constructs.md).  

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

## <a name="see-also"></a>Vea también  
 [Construcciones condicionales](../msbuild/msbuild-conditional-constructs.md)   
 [Referencia de esquemas de archivo del proyecto](../msbuild/msbuild-project-file-schema-reference.md)
