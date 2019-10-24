---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54b326116b1e1b677a997b264cf0c168a93febb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745265"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Describe una entrada en un mapa de direcciones.

## <a name="syntax"></a>Sintaxis

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Elementos
`rva` una dirección virtual relativa (RVA) en la imagen A.

`rvaTo` la dirección virtual relativa a la `rva` está asignada en la imagen B.

## <a name="remarks"></a>Comentarios
Un mapa de direcciones proporciona una traducción de un diseño de imagen (a) a otro (B). Matriz de estructuras `DiaAddressMapEntry` ordenadas por `rva` define un mapa de direcciones.

Para traducir una dirección, `addrA`, en la imagen a en una dirección, `addrB`, en la imagen B, realice los pasos siguientes:

1. Busque en el mapa la entrada, `e`, con el mayor `rva` menor o igual que `addrA`.

2. Establezca `delta = addrA - e.rva`.

3. Establezca `addrB = e.rvaTo + delta`.

    Una matriz de estructuras `DiaAddressMapEntry` se pasa al método [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .

## <a name="requirements"></a>Requisitos
Encabezado: Dia2. h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
