---
title: Elemento IDSymbol (IDSymbol Element) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d02a26a6874165738d917a14986d16d142c01915
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710375"
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
El `IDSymbol` elemento contiene el identificador del par GUID:ID que representa un menú, grupo o comando. El GUID procede `GuidSymbol` del elemento primario. El `IDSymbol` elemento `name` tiene un atributo que proporciona un nombre descriptivo `value` para el identificador, que se encuentra en el atributo.

## <a name="syntax"></a>Sintaxis

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|name|Necesario. Nombre del símbolo de ID.|
|value|Necesario. Valor de ID numérico del símbolo de ID.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contiene el GUID del par GUID:ID que representa un menú, grupo o comando. Agrupa los elementos `IDSymbol`.|

## <a name="remarks"></a>Observaciones
 Cada `IDSymbol` elemento de `GuidSymbol` un elemento `value`determinado debe tener un único . Sin `IDSymbol` embargo, los elementos que tienen valores idénticos pueden existir en un paquete siempre que tengan elementos primarios diferentes.

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
