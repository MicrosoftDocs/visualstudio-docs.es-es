---
title: Elemento ItemGroup (MSBuild) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 24
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 38c6099f912424d21df2aeea4cfdd0401ba57465
ms.openlocfilehash: e63c0dd4e201ef83f84f01148aacd4458806103d
ms.contentlocale: es-es
ms.lasthandoff: 07/14/2017

---
# Elemento ItemGroup (MSBuild)
<a id="itemgroup-element-msbuild" class="xliff"></a>
Contiene un conjunto de elementos [Item](../msbuild/item-element-msbuild.md) definidos por el usuario. Cada elemento que se utiliza en un proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] debe especificarse como elemento secundario de un elemento `ItemGroup`.  
  
 \<Project>  
 \<ItemGroup>  
  
## Sintaxis
<a id="syntax" class="xliff"></a>  
  
```xml  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## Atributos y elementos
<a id="attributes-and-elements" class="xliff"></a>  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos
<a id="attributes" class="xliff"></a>  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Condition`|Atributo opcional. Condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|  
  
### Elementos secundarios
<a id="child-elements" class="xliff"></a>  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|Define las entradas para el proceso de compilación. Puede haber cero o más elementos `Item` en un `ItemGroup`.|  
  
### Elementos primarios
<a id="parent-elements" class="xliff"></a>  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Proyecto](../msbuild/project-element-msbuild.md)|Elemento raíz necesario de un archivo de proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|[Target](../msbuild/target-element-msbuild.md)|A partir de .NET Framework 3.5, el elemento `ItemGroup` puede aparecer dentro de un elemento `Target`. Para obtener más información, consulte [Destinos](../msbuild/msbuild-targets.md).|  
  
## Comentarios
<a id="remarks" class="xliff"></a>  
  
## Ejemplo
<a id="example" class="xliff"></a>  
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
  
## Vea también
<a id="see-also" class="xliff"></a>  
 [Referencia de esquemas de archivo del proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementos](../msbuild/msbuild-items.md)   
 [Elementos comunes de proyectos de MSBuild](../msbuild/common-msbuild-project-items.md)
