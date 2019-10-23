---
title: IDiaEnumSymbolsByAddr::Prev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70265976e5c6e7c2b3f536f2b8648aaba44df528
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743852"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
Recupera los símbolos anteriores en orden por dirección.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Prev ( 
   ULONG        celt,
   IDiaSymbol** rgelt,
   ULONG*       pceltFetched
);
```

#### <a name="parameters"></a>Parámetros
 celt

de Número de símbolos del enumerador que se van a recuperar.

 rgelt

enuncia Matriz que se va a rellenar con objetos [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representan los símbolos deseados.

 pceltFetched

enuncia Devuelve el número de símbolos del enumerador recuperado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ningún símbolo anterior. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Este método actualiza la posición del enumerador por el número de elementos capturados.

## <a name="see-also"></a>Vea también
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)