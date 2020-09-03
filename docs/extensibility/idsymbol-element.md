---
title: Elemento IDSymbol | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710375"
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
El `IDSymbol` elemento contiene el identificador del par GUID: ID que representa un menú, grupo o comando. El GUID procede del elemento primario `GuidSymbol` . El `IDSymbol` elemento tiene un `name` atributo que proporciona un nombre descriptivo para el identificador, que se encuentra en el `value` atributo.

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
|value|Necesario. Valor de identificador numérico del símbolo de identificador.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contiene el GUID del par GUID: ID que representa un menú, grupo o comando. Agrupa los elementos `IDSymbol`.|

## <a name="remarks"></a>Observaciones
 Cada `IDSymbol` elemento de un `GuidSymbol` elemento determinado debe tener un único `value` . Sin embargo, `IDSymbol` los elementos que tienen valores idénticos pueden existir en un paquete siempre que tengan distintos elementos primarios.

## <a name="see-also"></a>Vea también
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
