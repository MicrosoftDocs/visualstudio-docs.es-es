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
ms.openlocfilehash: 1de2d6c9700dcb7b1106c3693d855bb1d8ae2cfa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738498"
---
# <a name="thunk_ordinal"></a>THUNK_ORDINAL
Designa tipos de código thunk.

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
Código thunk estándar de THUNK_ORDINAL_NOTYPE.

THUNK_ORDINAL_ADJUSTOR un código thunk del Ajustador de `this`.

Código thunk de llamada virtual de THUNK_ORDINAL_VCALL.

Código thunk de THUNK_ORDINAL_PCODE P.

Código thunk de carga retrasada de THUNK_ORDINAL_LOAD.

THUNK_ORDINAL_TRAMP_INCREMENTAL incremental Trampoline thunk (se usa un código thunk de Trampoline para rebotar las llamadas de un espacio de memoria a otro).

THUNK_ORDINAL_TRAMP_BRANCHISLAND punto de bifurcación Trampoline thunk.

## <a name="remarks"></a>Comentarios
Los valores de esta enumeración se devuelven desde una llamada al método [IDiaSymbol:: get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md) .

## <a name="requirements"></a>Requisitos
Encabezado: cvconst. h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)
