---
title: IDiaSession::symsAreEquiv | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0253104cf29e86825fadc8c8bd18133e0d3cf593
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839080"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Comprueba si dos símbolos son equivalentes.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>Parámetros
 `symbolA`

[in] La primera [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que se usa en la comparación.

 `symbolB`

[in] El segundo `IDiaSymbol` objeto que se usa en la comparación.

## <a name="return-value"></a>Valor devuelto
 Devuelve si los símbolos son equivalentes, `S_OK`; en caso contrario, devuelve `S_FALSE`, los símbolos no son equivalentes. En caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)