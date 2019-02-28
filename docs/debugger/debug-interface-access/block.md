---
title: Block | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagBlock symbol
- nested scopes
- Block symbol
ms.assetid: 95b7b0c1-ecc9-405f-8456-5f9cfb866498
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec30f353c9257643a750306828d76ad2f6f87a26
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56626263"
---
# <a name="block"></a>Bloque
Cada bloque de código se identifica mediante un `SymTagBlock` símbolos. Símbolos de bloque se usan para identificar los ámbitos anidados dentro de las funciones.

## <a name="properties"></a>Propiedades
 En la tabla siguiente muestra las propiedades que son válidas para este tipo de símbolo.

|Propiedad.|Tipo de datos|Descripción|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Parte del ajuste de ubicación; Para obtener más información, consulte el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte de la sección de ubicación; Para obtener más información, consulte el [LocationType (enumeración)](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Número de bytes de código del bloque.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo de la función o un bloque envolvente.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Devuelve el identificador del símbolo léxico primario.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Bloques tienen ubicaciones estáticas; Para obtener más información, consulte [ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Devuelve el nombre del bloque (que suele ser una cadena vacía).|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Devuelve la dirección virtual de este bloque en relación con su elemento primario léxico.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Id. de índice de símbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Devuelve `SymTagBlock` (uno de los [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) valores).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Devuelve la dirección virtual de este bloque dentro del archivo ejecutable.|

## <a name="see-also"></a>Vea también
- [Jerarquía léxica de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Enumeración LocationType](../../debugger/debug-interface-access/locationtype.md)
- [Ubicaciones de símbolos](../../debugger/debug-interface-access/symbol-locations.md)