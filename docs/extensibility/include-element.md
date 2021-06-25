---
title: Elemento Include | Microsoft Docs
description: El elemento Include especifica un archivo que se puede encontrar en la ruta de acceso de inclusión proporcionada para la inserción en el archivo actual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0005626c7fbb276775661a7cfb73d17f5e20d62
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899361"
---
# <a name="include-element"></a>Elemento Include
El elemento Include especifica un archivo que se puede encontrar en la ruta de acceso de inclusión proporcionada para la inserción en el archivo actual.  Todos los símbolos y tipos definidos pasarán a formar parte del resultado compilado.

## <a name="syntax"></a>Sintaxis

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|href|Necesario. Ruta de acceso al archivo de encabezado:<br /><br /> href="stdidcmd.h"|
|Condición|Opcional. Vea [Atributos condicionales.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|Ninguno.|Ninguno.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Define todos los elementos que representan comandos (es decir, elementos de menú, menús, barras de herramientas y cuadros combinados) que proporciona un VSPackage al IDE.|

## <a name="example"></a>Ejemplo

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Consulte también
- [Visual Studio de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
