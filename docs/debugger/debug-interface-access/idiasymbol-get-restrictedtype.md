---
title: IDiaSymbol::get_restrictedType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c48b00a6-26b0-47b0-b824-fe44dedbc756
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eac7e512d2fbfb5367725b3878d292444961b6de
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739391"
---
# <a name="idiasymbolget_restrictedtype"></a>IDiaSymbol::get_restrictedType
Especifica si el puntero de `this` se marca como restringido.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_restrictedType(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Puntero a un `BOOL` que especifica si el puntero de `this` se marca como restringido.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)