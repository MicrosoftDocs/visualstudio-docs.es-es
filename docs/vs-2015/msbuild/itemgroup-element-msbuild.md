---
title: Elemento ItemGroup (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
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
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f3a98238e922e08767524c361cdae850c40a4ba
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257691"
---
# <a name="itemgroup-element-msbuild"></a>Elemento ItemGroup (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Contiene un conjunto de elementos [Item](../msbuild/item-element-msbuild.md) definidos por el usuario. Cada elemento que se utiliza en un proyecto de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] debe especificarse como elemento secundario de un elemento `ItemGroup`.  
  
 \<Project>  
 \<ItemGroup>  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
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
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|Define las entradas para el proceso de compilación. Puede haber cero o más elementos `Item` en un `ItemGroup`.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Proyecto](../msbuild/project-element-msbuild.md)|Elemento raíz necesario de un archivo de proyecto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|[Target](../msbuild/target-element-msbuild.md)|A partir de .NET Framework 3.5, el elemento `ItemGroup` puede aparecer dentro de un elemento `Target`. Para obtener más información, consulte [Destinos](../msbuild/msbuild-targets.md).|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestran las colecciones de elementos definidos por el usuario `Res` y `CodeFiles` declaradas dentro de un elemento `ItemGroup`. Cada uno de los elementos de la colección de elementos `Res` contiene un elemento secundario [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) definido por el usuario.  
  
```  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquemas de archivo del proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementos](../msbuild/msbuild-items.md)   
 [Elementos comunes de proyectos de MSBuild](../msbuild/common-msbuild-project-items.md)



