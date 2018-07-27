---
title: Elemento ImportGroup | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ImportGroup> element [MSBuild]
- ImportGroup element [MSBuild]
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 184c7ee5fc5155b532243c51f85d8b5420892925
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079251"
---
# <a name="importgroup-element"></a>Elemento ImportGroup
Contiene una colección de elementos `Import` agrupados en una condición opcional. Para obtener más información, vea [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md).  

 \<Project>  
 \<ImportGroup>  

## <a name="syntax"></a>Sintaxis  

```xml  
<ImportGroup Condition="'String A' == 'String B'">  
    <Import ... />  
    <Import ... />  
</ImportGroup>  
```  

## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  

### <a name="attributes"></a>Atributos  

|Atributo|Descripción|  
|---------------|-----------------|  
|`Condition`|Atributo opcional.<br /><br /> La condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementos secundarios  

|Elemento|Descripción|  
|-------------|-----------------|  
|[Import](../msbuild/import-element-msbuild.md)|Importa el contenido de un archivo de proyecto en otro archivo de proyecto.|  

### <a name="parent-elements"></a>Elementos primarios  

|Elemento|Descripción|  
|-------------|-----------------|  
|[Proyecto](../msbuild/project-element-msbuild.md)|Elemento raíz necesario de un archivo de proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  

## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra el elemento `ImportGroup`.  

```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ImportGroup>  
        <Import Project="$(Targets1.targets) />  
        <Import Project="$(Targets2.targets) />  
    </ImportGroup>  
...  
</Project>  
```  

## <a name="see-also"></a>Vea también  
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementos](../msbuild/msbuild-items.md)
