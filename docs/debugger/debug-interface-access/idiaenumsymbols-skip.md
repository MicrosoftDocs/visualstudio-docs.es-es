---
title: IDiaEnumSymbols::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea2b1ea99eb2801259d58a12c359e9fffd887a64
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830441"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Omite un número especificado de símbolos en una secuencia de enumeración.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parámetros
 celt

[in] El número de símbolos en la secuencia de enumeración que se omitirán.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` si no hay ningún más símbolos que se omitirán.

## <a name="see-also"></a>Vea también
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)