---
title: Elemento ImportGroup | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa el elemento ImportGroup para que contenga una colección de elementos Import que se agrupan bajo una condición opcional.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e5ece72d83dd530a855d583ce061a22554d45a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914096"
---
# <a name="importgroup-element"></a>Elemento ImportGroup

  
Contiene una colección de elementos `Import` agrupados en una condición opcional. Para obtener más información, vea [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md).

```xml
<Project>
  <ImportGroup>
```

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
|[Importar](../msbuild/import-element-msbuild.md)|Importa el contenido de un archivo de proyecto en otro archivo de proyecto.|

### <a name="parent-elements"></a>Elementos primarios

| Elemento | Descripción |
| - | - |
| [Proyecto](../msbuild/project-element-msbuild.md) | Elemento raíz necesario de un archivo de proyecto de MSBuild. |

## <a name="example"></a>Ejemplo

 En el ejemplo de código siguiente se muestra el elemento `ImportGroup`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ImportGroup>
        <Import Project="$(Targets1.targets)" />
        <Import Project="$(Targets2.targets)" />
    </ImportGroup>
...
</Project>
```

## <a name="see-also"></a>Vea también

- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
- [Elementos](../msbuild/msbuild-items.md)
