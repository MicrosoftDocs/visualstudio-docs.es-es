---
title: GuidSymbol (elemento) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bebcec561f915bd8223d0adc183293a1760c261d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342210"
---
# <a name="guidsymbol-element"></a>GuidSymbol (elemento)
El `GuidSymbol` elemento contiene el GUID del par GUID: ID que representa un menú, grupo o comando. El Id. de procede de un `IDSymbol` elemento en el `GuidSymbol` elemento. El `GuidSymbol` elemento tiene un `name` atributo que proporciona un nombre descriptivo para el GUID, que se encuentra en la `value` atributo.

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
|name|Obligatorio. Nombre del símbolo GUID.|
|value|Obligatorio. GUID del símbolo GUID.|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[IDSymbol (elemento)](../extensibility/idsymbol-element.md)|Contiene el identificador del par GUID: ID que representa un menú, grupo o comando.|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Symbols (elemento)](../extensibility/symbols-element.md)|Grupos `GuidSymbol` elementos en un *.vsct* archivo.|

## <a name="remarks"></a>Comentarios
 Normalmente, un *.vsct* archivo contiene tres `GuidSymbol` elementos en su `Symbols` sección, uno para el propio paquete, uno para el conjunto de comandos (la colección de los menús, grupos y comandos que pone a disposición del paquete), y uno de los mapas de bits que proporcionan iconos para los botones y otros componentes visuales. Cada `IDSymbol` elemento en un determinado `GuidSymbol` elemento debe tener un único `value`. Sin embargo, `IDSymbol` los elementos que tienen valores idénticos pueden existir en un paquete, siempre y cuando tengan que diferentes objetos primarios.

## <a name="see-also"></a>Vea también
- [Archivos visuales Studio comando table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)