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
ms.openlocfilehash: 8414788af44d78943088b78b2d3e42a5a8d8c50b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745025"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
Proporciona un mapa de direcciones para admitir las traducciones del diseño de la imagen.

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

de Número de elementos del parámetro `data`.

 `data[]`

de Matriz de estructuras de [estructura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) que definen el mapa de traslación.

 `imagetoSymbols`

[in] `TRUE` si el parámetro `data` define una asignación del nuevo diseño de imagen al diseño original (como se describe en los símbolos de depuración). `FALSE` si `data` es un mapa del nuevo diseño de imagen tomado del diseño original.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Normalmente, el DIA recupera las asignaciones de traducción de direcciones del archivo de base de datos de programa (. pdb). Si faltan estos valores, se llama al método [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) dos veces, una vez con el parámetro `imagetoSymbols` establecido en `TRUE` y una vez con el parámetro `imagetoSymbols` establecido en `FALSE`. Las traducciones de mapa de direcciones no se pueden habilitar con el método [IDiaAddressMap::P ut_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) , a menos que se proporcionen ambos mapas de traducción.

## <a name="see-also"></a>Vea también
- [Estructura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)