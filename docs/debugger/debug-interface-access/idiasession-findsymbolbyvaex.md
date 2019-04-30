---
title: IDiaSession::findSymbolByVAEx | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByVAEx method
ms.assetid: 11c685f6-cda2-4474-a432-214ecaae4ffa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16b62c5efb520e90606d6311b60a839404359720
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832368"
---
# <a name="idiasessionfindsymbolbyvaex"></a>IDiaSession::findSymbolByVAEx
Recupera un tipo de símbolo especificado que contiene, o más cercana a una dirección virtual especificado (VA) y el desplazamiento.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT findSymbolByVAEx ( 
   ULONGLONG    va,
   SymTagEnum   symtag,
   IDiaSymbol** ppSymbol,
   LONG*        displacement
);
```

#### <a name="parameters"></a>Parámetros
 `va`

[in] Especifica el jefe

 `symtag`

[in] Tipo de símbolo que se encuentra. Los valores se toman de la [SymTagEnum (enumeración)](../../debugger/debug-interface-access/symtagenum.md) enumeración.

 `ppSymbol`

[out] Devuelve un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recupera el objeto que representa el símbolo.

 `displacement`

[out] Devuelve un valor que especifica un desplazamiento desde la dirección virtual proporcionada por `va`.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo

```C++
IDiaSymbol* pFunc;
LONG disp = 0;
pSession->findSymbolByVAEx( va, SymTagFunction, &pFunc, &disp );
```

## <a name="see-also"></a>Vea también
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)