---
title: Elemento GuidSymbol | Microsoft Docs
description: El elemento GuidSymbol contiene el GUID del par GUID:ID que representa un menú, un grupo o un comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7c30c7a48b03b5deed3267e106e926d3cb5114c1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902766"
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
El `GuidSymbol` elemento contiene el GUID del par GUID:ID que representa un menú, un grupo o un comando. El identificador procede de `IDSymbol` un elemento del elemento `GuidSymbol` . El `GuidSymbol` elemento tiene un atributo que proporciona un nombre descriptivo para el `name` GUID, que se encuentra en el atributo `value` .

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
|valor|Necesario. GUID del símbolo GUID.|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contiene el identificador del par GUID:ID que representa un menú, un grupo o un comando.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Symbols](../extensibility/symbols-element.md)|Agrupa `GuidSymbol` los elementos de un archivo *.vsct.*|

## <a name="remarks"></a>Observaciones
 Normalmente, un archivo *.vsct* contiene tres elementos en su sección, uno para el propio paquete, otro para el conjunto de comandos (la colección de menús, grupos y comandos que el paquete pone a disposición) y otro para los mapas de bits que proporcionan iconos para botones y otros componentes `GuidSymbol` `Symbols` visuales. Cada `IDSymbol` elemento de un elemento determinado debe tener un único `GuidSymbol` `value` . Sin embargo, los elementos que tienen valores idénticos pueden `IDSymbol` existir en un paquete siempre que tengan elementos principales diferentes.

## <a name="see-also"></a>Consulta también
- [Visual Studio de tabla de comandos (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
