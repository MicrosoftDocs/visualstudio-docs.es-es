---
title: IDiaAddressMap::set_addressMap | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 963ee64b639780bae60a4c2655db8b666d87c702
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62554253"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
Proporciona un mapa de direcciones para admitir las traducciones de diseño de imagen.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT set_addressMap ( 
   DWORD                     cbData,
   struct DiaAddressMapEntry data[],
   BOOL                      imagetoSymbols
);
```

#### <a name="parameters"></a>Parámetros
 `cbData`

[in] El número de elementos de la `data` parámetro.

 `data[]`

[in] Una matriz de [DiaAddressMapEntry estructura](../../debugger/debug-interface-access/diaaddressmapentry.md) estructuras que definen la asignación de traducción.

 `imagetoSymbols`

[in] `TRUE` si el `data` parámetro define una asignación desde el nuevo diseño de la imagen al diseño original (como se describe en los símbolos de depuración). `FALSE` Si `data` es un mapa para el nuevo diseño de imagen procedente del diseño original.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Normalmente, el DIA recupera asignaciones de traducción de direcciones desde el archivo de programa (.pdb) de la base de datos. Si faltan estos valores, el [Set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) se llama al método dos veces, una vez con el `imagetoSymbols` parámetro establecido en `TRUE` y una vez con el `imagetoSymbols` parámetro establecido en `FALSE`. Traducciones de asignación de direcciones no pueden habilitarse mediante la [Put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) método a menos que se proporcionan ambos mapas de traducción.

## <a name="see-also"></a>Vea también
- [Estructura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)