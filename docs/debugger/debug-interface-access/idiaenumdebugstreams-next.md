---
title: IDiaEnumDebugStreams::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Next method
ms.assetid: eb8eae5a-be27-45f4-a7bd-6e4ef0652385
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1b7819c90804933795c220c4d47f288d29abfe1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616565"
---
# <a name="idiaenumdebugstreamsnext"></a>IDiaEnumDebugStreams::Next
Recupera un número especificado de secuencias de depuración en la secuencia de enumeración.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Next ( 
   ULONG                     celt,
   IDiaEnumDebugStreamData** rgelt,
   ULONG*                    pceltFetched
);
```

#### <a name="parameters"></a>Parámetros
 celt

[in] El número de secuencias de depuración en el enumerador que se va a recuperar.

 rgelt

[out] Devuelve una matriz de [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) transmite por secuencias que se va a recuperar objetos que representan la depuración.

 pceltFetched

[out] Devuelve el número de secuencias de depuración que se devuelve.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay más secuencias. De lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)