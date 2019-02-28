---
title: Findsymbolbyrvaex | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVAEx method
ms.assetid: 61344966-fed4-4c02-9e27-20356ec2ef7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c6c8e3523a49bd4fc22a86c9ec86b1e8cd2038e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56634089"
---
# <a name="idiasessionfindsymbolbyrvaex"></a>IDiaSession::findSymbolByRVAEx
Recupera un tipo de símbolo especificado que contiene, o más cercana a una dirección virtual relativa (RVA) especificado y el desplazamiento.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT findSymbolByRVAEx ( 
   DWORD        rva,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol,
   LONG*        displacement
);
```

#### <a name="parameters"></a>Parámetros
 `rva`

[in] Especifica la dirección RVA.

 `symtag`

[in] Tipo de símbolo que se encuentra. Los valores se toman de la [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) enumeración.

 `ppSymbol`

[out] Devuelve un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recupera el objeto que representa el símbolo.

 `displacement`

[out] Devuelve un valor que especifica un desplazamiento de la dirección virtual relativa especificada en `rva`.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo

```C++
IDiaSymbol* pFunc;
LONG disp = 0;
pSession->findSymbolByRVAEx( rva, SymTagFunction, &pFunc, &disp );
```

## <a name="see-also"></a>Vea también
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)