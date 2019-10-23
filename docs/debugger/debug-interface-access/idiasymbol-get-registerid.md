---
title: IDiaSymbol::get_registerId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ffd349b56c4292de04d5d7a38e82eeafed6775e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739460"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
Recupera el designador de registro de la ubicación cuando la [enumeración LocationType (](../../debugger/debug-interface-access/locationtype.md) se establece en `LocIsEnregistered`.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_registerId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve el designador de registro de la ubicación.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
 Si el símbolo es relativo a un registro, es decir, si la [enumeración LocationType (](../../debugger/debug-interface-access/locationtype.md) del símbolo está establecida en `LocIsRegRel`, use el método `get_registerId` seguido de una llamada al método [IDiaSymbol:: get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) para obtener el desplazamiento del registro donde el símbolo es. localizado.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración LocationType](../../debugger/debug-interface-access/locationtype.md)