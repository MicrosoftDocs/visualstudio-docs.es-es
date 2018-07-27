---
title: Elemento ItemMetadata (MSBuild) | Microsoft Docs
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
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 78e9bfffc38ac54ec7aeb525665dc7e3a8927f74
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080494"
---
# <a name="itemmetadata-element-msbuild"></a>Elemento ItemMetadata (MSBuild)
Contiene una clave de metadatos de elemento definida por el usuario que incluye el valor de metadatos del elemento. Un elemento puede tener cualquier número de pares clave-valor de metadatos.  

 \<Project>  
 \<ItemGroup>  
 \<Item>  

## <a name="syntax"></a>Sintaxis  

```xml  
<ItemMetadataName> Item Metadata value</ItemMetadataName>  
```  

## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  

### <a name="attributes"></a>Atributos  

|Atributo|Descripción|  
|---------------|-----------------|  
|`Condition`|Atributo opcional.<br /><br /> Condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  

### <a name="parent-elements"></a>Elementos primarios  

|Elemento|Descripción|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|Un elemento definido por el usuario que define las entradas para el proceso de compilación.|  

## <a name="text-value"></a>Valor de texto  
 El valor de texto es opcional.  

 Este texto especifica el valor de metadatos del elemento, que puede ser texto o XML.  

## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo agregar los metadatos `Culture` con el valor `fr` al elemento `CSFile`.  

```xml  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  

## <a name="see-also"></a>Vea también  
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elementos](../msbuild/msbuild-items.md)
