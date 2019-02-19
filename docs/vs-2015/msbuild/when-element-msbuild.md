---
title: Elemento When (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#When
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <When> Element [MSBuild]
- When Element [MSBuild]
ms.assetid: eb27de6f-4e71-4e87-87e2-d93f7bf5899c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 93fd259e00d7a8f849b97cb97c3f950cd95f57ed
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54761547"
---
# <a name="when-element-msbuild"></a>Elemento When (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Especifica un posible bloque de código que el elemento `Choose` puede seleccionar.  
  
 \<Project>  
 \<Choose>  
 \<When>  
 \<Choose>  
 ...  
 \<Otherwise>  
 \<Choose>  
 ...  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<When Condition="'StringA'=='StringB'">  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Choose>... </Choose>  
</When>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|Condición|Atributo necesario.<br /><br /> Condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Elemento opcional.<br /><br /> Evalúa los elementos secundarios para seleccionar una sección de código y ejecutarla. Puede haber cero o más elementos `Choose` en un elemento `When`.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento opcional.<br /><br /> Contiene un conjunto de elementos [Item](../msbuild/item-element-msbuild.md) definidos por el usuario. Puede haber cero o más elementos `ItemGroup` en un elemento `When`.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento opcional.<br /><br /> Contiene un conjunto de elementos [Property](../msbuild/property-element-msbuild.md) definidos por el usuario. Puede haber cero o más elementos `PropertyGroup` en un elemento `When`.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Elemento Choose (MSBuild)](../msbuild/choose-element-msbuild.md)|Evalúa los elementos secundarios para seleccionar una sección de código y ejecutarla.|  
  
## <a name="remarks"></a>Comentarios  
 Si el atributo `Condition` se evalúa en true, los elementos secundarios `ItemGroup` y `PropertyGroup` del elemento `When` se ejecutarán y todos los elementos subsiguientes `When` se omitirán.  
  
 Los elementos `Choose`, `When` y `Otherwise` se utilizan juntos para ofrecer un modo de seleccionar una sección de código para que ejecute una serie de alternativas posibles. Para obtener más información, consulte la sección [Construcciones condicionales](../msbuild/msbuild-conditional-constructs.md).  
  
## <a name="example"></a>Ejemplo  
 En el proyecto siguiente se utiliza el elemento `Choose` para seleccionar el conjunto de valores de propiedad de los elementos `When` que desea establecer. Si los atributos `Condition` de ambos elementos `When` se evalúan como `false`, se establecen los valores de propiedad del elemento `Otherwise`.  
  
```  
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
