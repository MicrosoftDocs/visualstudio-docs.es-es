---
title: IDSymbol (elemento) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4489be4ea24382ddaf0fcbe5e824eac3945c9cec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319535"
---
# <a name="idsymbol-element"></a>IDSymbol (elemento)
El `IDSymbol` elemento contiene el identificador del par GUID: ID que representa un menú, grupo o comando. Incluye el GUID del elemento primario `GuidSymbol` elemento. El `IDSymbol` elemento tiene un `name` atributo que proporciona un nombre descriptivo para el identificador, que se encuentra en la `value` atributo.

## <a name="syntax"></a>Sintaxis

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|name|Obligatorio. Nombre del símbolo de identificador.|
|value|Obligatorio. Valor de identificador numérico del símbolo de identificador.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[GuidSymbol (elemento)](../extensibility/guidsymbol-element.md)|Contiene el GUID del par GUID: ID que representa un menú, grupo o comando. Agrupa los elementos `IDSymbol`.|

## <a name="remarks"></a>Comentarios
 Cada `IDSymbol` elemento en un determinado `GuidSymbol` elemento debe tener un único `value`. Sin embargo, `IDSymbol` los elementos que tienen valores idénticos pueden existir en un paquete, siempre y cuando tengan que diferentes objetos primarios.

## <a name="see-also"></a>Vea también
- [Archivos visuales Studio comando table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)