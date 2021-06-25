---
title: Elemento IDSymbol | Microsoft Docs
description: El elemento IDSymbol contiene el identificador del par GUID:ID que representa un menú, un grupo o un comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e5158b16fb2d12a7d1a93c0296126e915a138269
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904947"
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
El `IDSymbol` elemento contiene el identificador del par GUID:ID que representa un menú, un grupo o un comando. El GUID procede del elemento `GuidSymbol` primario. El `IDSymbol` elemento tiene un atributo que proporciona un nombre descriptivo para el `name` identificador, que se encuentra en el atributo `value` .

## <a name="syntax"></a>Sintaxis

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|name|Necesario. Nombre del símbolo de identificador.|
|valor|Necesario. Valor de id. numérico del símbolo de identificador.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contiene el GUID del par GUID:ID que representa un menú, un grupo o un comando. Agrupa los elementos `IDSymbol`.|

## <a name="remarks"></a>Observaciones
 Cada `IDSymbol` elemento de un elemento determinado debe tener un único `GuidSymbol` `value` . Sin embargo, los elementos que tienen valores idénticos pueden `IDSymbol` existir en un paquete siempre que tengan elementos principales diferentes.

## <a name="see-also"></a>Consulta también
- [Visual Studio de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
