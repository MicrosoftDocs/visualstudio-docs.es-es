---
title: Elemento GuidSymbol | Microsoft Docs
description: 'El elemento GuidSymbol contiene el GUID del par GUID: ID que representa un menú, un grupo o un comando.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb683c99614797fa8b05eae87c758ec33f675c99
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057460"
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
El `GuidSymbol` elemento contiene el GUID del par GUID: ID que representa un menú, un grupo o un comando. El identificador procede de un `IDSymbol` elemento del `GuidSymbol` elemento. El `GuidSymbol` elemento tiene un `name` atributo que proporciona un nombre descriptivo para el GUID, que se encuentra en el `value` atributo.

## <a name="syntax"></a>Sintaxis

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|name|Necesario. Nombre del símbolo GUID.|
|value|Necesario. GUID del símbolo GUID.|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contiene el identificador del par GUID: ID que representa un menú, grupo o comando.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Symbols](../extensibility/symbols-element.md)|Agrupa `GuidSymbol` los elementos de un archivo *. Vsct* .|

## <a name="remarks"></a>Observaciones
 Normalmente, un archivo *. Vsct* contiene tres `GuidSymbol` elementos en su `Symbols` sección, uno para el propio paquete, uno para el conjunto de comandos (la colección de menús, grupos y comandos que el paquete pone a disposición) y otro para los mapas de bits que proporcionan iconos para botones y otros componentes visuales. Cada `IDSymbol` elemento de un `GuidSymbol` elemento determinado debe tener un único `value` . Sin embargo, `IDSymbol` los elementos que tienen valores idénticos pueden existir en un paquete siempre que tengan distintos elementos primarios.

## <a name="see-also"></a>Consulte también
- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
