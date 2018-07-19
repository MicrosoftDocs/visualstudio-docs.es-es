---
title: Elemento Sdk (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 01/25/2018
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d674e7613898816f905e0d0a11bdc2484cf4f25
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325328"
---
# <a name="sdk-element-msbuild"></a>Elemento Sdk (MSBuild)
Hace referencia a un SDK de proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

 \<Project>  
 \<Sdk>  


## <a name="syntax"></a>Sintaxis  

```xml  
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />  
```  

## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  

### <a name="attributes"></a>Atributos  

|Atributo|Descripción|  
|---------------|-----------------|  
|`Name`|Atributo necesario.<br /><br /> Nombre del SDK del proyecto.|  
|`Version`|Atributo opcional.<br /><br /> Versión del SDK del proyecto.|  

### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios  
 |Elemento|Descripción|  
|-------------|-----------------|  
|[Proyecto](../msbuild/project-element-msbuild.md)|Elemento raíz necesario de un archivo de proyecto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] .|  

## <a name="see-also"></a>Vea también  
 [Referencia a un SDK de un proyecto de MSBuild](../msbuild/how-to-use-project-sdk.md)   
 [Referencia de esquemas de archivo del proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
