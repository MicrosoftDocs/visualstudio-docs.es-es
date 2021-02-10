---
title: Elemento Sdk (MSBuild) | Microsoft Docs
description: Obtenga información sobre la sintaxis, los atributos y los elementos del elemento Sdk de MSBuild, que hace referencia a un SDK de proyecto de MSBuild.
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cd5f66cc6500a3320e0da962985f5b7fff1e86dc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937906"
---
# <a name="sdk-element-msbuild"></a>Elemento Sdk (MSBuild)

Hace referencia a un SDK de un proyecto de MSBuild.

 \<Project> \<Sdk>

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

| Elemento | Descripción |
| - | - |
| [Proyecto](../msbuild/project-element-msbuild.md) | Elemento raíz necesario de un archivo de proyecto de MSBuild. |

## <a name="see-also"></a>Consulte también

- [Procedimiento: Hacer referencia a un SDK de un proyecto de MSBuild](../msbuild/how-to-use-project-sdk.md)
- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
