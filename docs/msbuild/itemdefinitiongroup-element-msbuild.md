---
title: "Elemento ItemDefinitionGroup (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<ItemDefinitionGroup> (elemento) [MSBuild]"
  - "ItemDefinitionGroup (elemento) [MSBuild]"
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Elemento ItemDefinitionGroup (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El elemento  `ItemDefinitionGroup` permite definir un conjunto de definiciones de elementos, que son los valores de los metadatos que se aplican a todos los elementos del proyecto de forma predeterminada.  ItemDefinitionGroup elimina la necesidad de utilizar [CreateItem \(Tarea\)](../msbuild/createitem-task.md) y [CreateProperty \(Tarea\)](../msbuild/createproperty-task.md).  Para obtener más información, vea [Definiciones de elementos](../msbuild/item-definitions.md).  
  
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
|[Elemento](../msbuild/item-element-msbuild.md)|Define las entradas para el proceso de compilación.  Puede haber cero o más elementos `Item` en un `ItemDefinitionGroup`.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Proyecto](../msbuild/project-element-msbuild.md)|Elemento raíz necesario de un archivo de proyecto de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  
  
## Ejemplo  
 El ejemplo de código siguiente define dos elementos de metadatos, m y n, en ItemDefinitionGroup.  En este ejemplo, los metadatos predeterminados "m" se aplican al elemento "i" porque los metadatos "m" no están definidos explícitamente por el elemento "i".  Sin embargo, los metadatos predeterminados "n" no se aplican al elemento "i" porque los metadatos "n" ya están definidos por el elemento "i".  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemDefinitionGroup>  
        <i>  
            <m>m1</m>  
            <n>n1</n>  
        </i>        
    </ItemDefinitionGroup>  
    <ItemGroup>  
        <i Include="a">  
            <o>o1</o>  
            <n>n2</n>  
        </i>  
    </ItemGroup>  
    ...  
</Project>  
```  
  
## Vea también  
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [elementos](../msbuild/msbuild-items.md)