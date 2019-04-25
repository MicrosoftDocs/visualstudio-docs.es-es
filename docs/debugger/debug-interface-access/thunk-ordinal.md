---
title: THUNK_ORDINAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Thunk_Ordinal enumeration
ms.assetid: 026f98a9-36b8-41ef-8a72-12d7cbc2d362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 776ee35e57b62463d47fc6f7fa26133f507f16f9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613276"
---
# <a name="thunkordinal"></a>THUNK_ORDINAL
Designa los tipos de código thunk.

## <a name="syntax"></a>Sintaxis

```C++
typedef enum THUNK_ORDINAL {
    THUNK_ORDINAL_NOTYPE,
    THUNK_ORDINAL_ADJUSTOR,
    THUNK_ORDINAL_VCALL,
    THUNK_ORDINAL_PCODE,
    THUNK_ORDINAL_LOAD

    // trampoline thunk ordinals - only for use in Trampoline thunk symbols
    THUNK_ORDINAL_TRAMP_INCREMENTAL,
    THUNK_ORDINAL_TRAMP_BRANCHISLAND,
} THUNK_ORDINAL;
```

## <a name="elements"></a>Elementos
Thunk THUNK_ORDINAL_NOTYPE estándar.

Un THUNK_ORDINAL_ADJUSTOR `this` código thunk ajustador.

THUNK_ORDINAL_VCALL Virtual código thunk de llamada.

Código thunk de código empaquetado THUNK_ORDINAL_PCODE.

Código thunk de carga de retraso THUNK_ORDINAL_LOAD.

THUNK_ORDINAL_TRAMP_INCREMENTAL Incremental código thunk de cama elástica (un código thunk de cama elástica se usa para hacer rebotar la llamadas desde el espacio de memoria de uno a otro).

Código thunk de rama THUNK_ORDINAL_TRAMP_BRANCHISLAND punto cama elástica.

## <a name="remarks"></a>Comentarios
Los valores de esta enumeración se devuelven en una llamada a la [Get_thunkordinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) método.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst.h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
