---
title: Elemento ItemDefinitionGroup (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91a98d16e755daeb3fb514a47a741f5ac99abe12
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793011"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>Elemento ItemDefinitionGroup (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El elemento `ItemDefinitionGroup` permite definir un conjunto de definiciones de elementos, que son valores de metadatos que, de forma predeterminada, se aplican a todos los elementos del proyecto. Con ItemDefinitionGroup, ya no es necesario usar la [tarea CreateItem](../msbuild/createitem-task.md) ni la [tarea CreateProperty](../msbuild/createproperty-task.md). Para obtener más información, consulte [Definiciones de elementos](../msbuild/item-definitions.md).  
  
 \<Project>  
 \<ItemDefinitionGroup>  
  
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
|[Item](../msbuild/item-element-msbuild.md)|Define las entradas para el proceso de compilación. Puede haber cero o más elementos `Item` en un `ItemDefinitionGroup`.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Proyecto](../msbuild/project-element-msbuild.md)|Elemento raíz necesario de un archivo de proyecto [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se definen dos elementos de metadatos, m y n, en ItemDefinitionGroup. En este ejemplo, los metadatos predeterminados "m" se aplican al elemento "i" porque los metadatos "m" no están definidos explícitamente por el elemento "i". Sin embargo, los metadatos predeterminados "n" no se aplican al elemento "i" porque los metadatos "n" ya están definidos por el elemento "i".  
  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia de esquemas de archivo del proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementos](../msbuild/msbuild-items.md)
