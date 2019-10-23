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
ms.openlocfilehash: 61cfc582f11670af8c956c3334681284ce5172a6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741861"
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

de Primer objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) usado en la comparación.

 `symbolB`

de Segundo objeto de `IDiaSymbol` utilizado en la comparación.

## <a name="return-value"></a>Valor devuelto
 Si los símbolos son equivalentes, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE`, los símbolos no son equivalentes. De lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)