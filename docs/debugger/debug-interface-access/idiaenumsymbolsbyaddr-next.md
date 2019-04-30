---
title: IDiaEnumSymbolsByAddr::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e52567eddcbb6c4f372256e66b7b723bc7aa7394
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833446"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
Recupera los símbolos en el orden siguientes por dirección.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Next ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parámetros
 celt

[in] El número de símbolos en el enumerador que se va a recuperar.

 rgelt

[out] Una matriz que se va a rellenar con el [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objetos que representan los símbolos deseados.

 pceltFetched

[out] Devuelve el número de símbolos en el enumerador capturado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ningún símbolo más. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método actualiza la posición del enumerador por el número de elementos que se capturan.

## <a name="see-also"></a>Vea también
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)