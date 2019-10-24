---
title: IDiaSymbol::get_targetRelativeVirtualAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_targetRelativeVirtualAddress method
ms.assetid: 49a159f3-6943-44d3-90a3-0dba51e8a7ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c51a946ed6b78220846e779f9849d3b8ae9fd20d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739188"
---
# <a name="idiasymbolget_targetrelativevirtualaddress"></a>IDiaSymbol::get_targetRelativeVirtualAddress
Recupera la dirección virtual relativa (RVA) de un destino de código thunk.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_targetRelativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve la RVA de un destino de código thunk.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
 Esta propiedad solo es válida si el símbolo es un valor de [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md) de `SymTagThunk`.

 Un "thunk" es un fragmento de código que convierte entre un espacio de direcciones de memoria de 32 bits (también conocido como espacio de direcciones plano) y un espacio de direcciones de 16 bits (conocido como espacio de direcciones segmentado).

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)