---
title: IDiaSymbol::get_oemSymbolId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemSymbolId method
ms.assetid: 187801f0-bd82-4c5b-9fae-8eeb1a4ac0ce
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0a08b29c3d1dae8b79650f450faaf8b9e1d452a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399563"
---
# <a name="idiasymbolgetoemsymbolid"></a>IDiaSymbol::get_oemSymbolId
Recupera el valor de Id. del símbolo de fabricante de equipos originales (OEM).

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_oemSymbolId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

[out] Devuelve que un OEM asignado internamente de símbolos identificador.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
 El identificador es un valor único creado mediante el SDK de DIA para marcar todos los símbolos como único.

 Esta propiedad solo se aplica a los símbolos con un [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) el tipo de `SymTagCustomType`.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)