---
title: IDiaEnumStackFrames::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9cf220c65cf11836e64a7e1f4c0142c89669f4b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62833315"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Recupera un número especificado de elementos de marco de pila de la secuencia de enumeración.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Next( 
   ULONG             celt,
   IDiaStackFrame**  rgelt,
   ULONG*            pceltFetched
);
```

#### <a name="parameters"></a>Parámetros
 celt

[in] El número de elementos de stackframe del enumerador que se va a recuperar.

 rgelt

[out] Una matriz que se rellena con la solicitada [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) objetos.

 pceltFetched

[out] Devuelve al número de la pila de elementos de marco en el enumerador capturado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ningún más marcos de pila. De lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)