---
title: "Elemento ItemGroup (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemGroup (elemento) [MSBuild]"
  - "Elemento <ItemGroup> [MSBuild]"
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elemento ItemGroup (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene un conjunto de elementos [Item](../msbuild/item-element-msbuild.md) definidos por el usuario.  Cada elemento utilizado en un proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] debe especificarse como elemento secundario de un elemento `ItemGroup`.  
  
## Sintaxis  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Condition`|Atributo opcional.  Condición que se va a evaluar.  Para obtener más información, vea [Condiciones](../msbuild/msbuild-conditions.md).|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento](../msbuild/item-element-msbuild.md)|Define las entradas para el proceso de compilación.  Puede haber cero o más elementos `Item` en un `ItemGroup`.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Proyecto](../msbuild/project-element-msbuild.md)|Elemento raíz necesario de un archivo de proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
|[Destino](../msbuild/target-element-msbuild.md)|A partir de .NET Framework 3.5, el elemento `ItemGroup` puede aparecer dentro de un elemento `Target`.  Para obtener más información, vea [Destinos](../msbuild/msbuild-targets.md).|  
  
## Comentarios  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestran las colecciones de elementos `Res` y `CodeFiles` definidas por el usuario declaradas dentro de un elemento `ItemGroup`.  Cada uno de los elementos en la colección de elementos `Res` contiene un elemento [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md) secundario definido por el usuario.  
  
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
  
## Vea también  
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [elementos](../msbuild/msbuild-items.md)   
 [Elementos comunes de proyectos de MSBuild](../msbuild/common-msbuild-project-items.md)