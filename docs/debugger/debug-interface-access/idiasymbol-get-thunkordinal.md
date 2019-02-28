---
title: IDiaSymbol::get_thunkOrdinal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78ce8311e9504261399f22feefebb93fb9b3c64f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605957"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
Recupera el tipo de código thunk de una función.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_thunkOrdinal ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

[out] Devuelve un valor de la [THUNK_ORDINAL (enumeración)](../../debugger/debug-interface-access/thunk-ordinal.md) enumeración que especifica el tipo de código thunk de una función.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
 Esta propiedad es válida solo si el símbolo como un [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) valor `SymTagThunk`.

 Un "código thunk" es un fragmento de código que convierte entre un espacio de direcciones de memoria de 32 bits (también conocido como espacio de direcciones sin formato) y un espacio de direcciones de 16 bits (conocido como un espacio de direcciones segmentados).

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)
- [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)