---
title: IDiaEnumSegments::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9b0f0d06ae5303277c296fd56e36e60b9a6f022
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829646"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Recupera un número especificado de segmentos de la secuencia de enumeración.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Next ( 
   ULONG         celt,
   IDiaSegment** rgelt,
   ULONG*        pceltFetched
);
```

#### <a name="parameters"></a>Parámetros
 celt

[in] El número de segmentos en el enumerador que se va a recuperar.

 rgelt

[out] Una matriz que se rellena con los deseados [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objetos que representan los segmentos.

 pceltFetched

[out] Devuelve el número de segmentos en el enumerador capturado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no existen más segmentos. De lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)