---
title: IDiaEnumSegments::Item | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87751dcca1e2109db53c9d6dd4594bc969ffc684
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833277"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
Recupera un segmento por medio de un índice.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Item ( 
   DWORD         index,
   IDiaSegment** segment
);
```

#### <a name="parameters"></a>Parámetros
 índice

[in] Índice de la [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objeto va a recuperar. El índice está en el intervalo de 0 a `count`-1, donde `count` devuelto por la [Idiaenumsegments](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) método.

 segment

[out] Devuelve un [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objeto que representa el segmento deseado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)