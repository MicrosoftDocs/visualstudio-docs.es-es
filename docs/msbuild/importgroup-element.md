---
title: Elemento ImportGroup | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ImportGroup> element [MSBuild]
- ImportGroup element [MSBuild]
ms.assetid: dac3fa2d-6678-4017-af35-93686f53f302
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: df9aebf8e604ad16b99ac458bdd9d143bd461ff7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="importgroup-element"></a>Elemento ImportGroup
Contiene una colección de elementos `Import` agrupados en una condición opcional. Para obtener más información, vea [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md).  

 \<Project>  
 \<ImportGroup>  

## <a name="syntax"></a>Sintaxis  

```  
<ImportGroup Condition="'String A' == 'String B'">  
    <Import ... />  
    <Import ... />  
</ImportGroup>  
```  

## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  

### <a name="attributes"></a>Atributos  

|Atributo|Description|  
|---------------|-----------------|  
|`Condition`|Atributo opcional.<br /><br /> La condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementos secundarios  

|Elemento|Description|  
|-------------|-----------------|  
|[Import](../msbuild/import-element-msbuild.md)|Importa el contenido de un archivo de proyecto en otro archivo de proyecto.|  

### <a name="parent-elements"></a>Elementos primarios  

|Elemento|Description|  
|-------------|-----------------|  
|[Proyecto](../msbuild/project-element-msbuild.md)|Elemento raíz necesario de un archivo de proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  

## <a name="remarks"></a>Comentarios  

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
 [Referencia de esquemas de archivo del proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementos](../msbuild/msbuild-items.md)
