---
title: IDiaSession::symbolById | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b58fcf55741975a776e222b2845ae50774e7fc9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832920"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
Recupera un símbolo por su identificador único.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT symbolById (
    DWORD        id,
    IDiaSymbol** ppSymbol
);
```

#### <a name="parameters"></a>Parámetros
`id`

[in] Identificador único.

`ppSymbol`

[out] Devuelve un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recupera el objeto que representa el símbolo.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
El identificador especificado es un valor único utilizado internamente por el SDK de DIA para todos los símbolos que sea única.

Este método puede usarse, por ejemplo, para recuperar el símbolo que representa el tipo de otro símbolo (vea el ejemplo).

## <a name="example"></a>Ejemplo
Este ejemplo recupera una [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el tipo de símbolo de otro. En este ejemplo se muestra cómo usar el `symbolById` método en la sesión. Un enfoque más sencillo es llamar a la [Get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) método para recuperar el símbolo de tipo directamente.

```C++
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)
{
    IDiaSymbol *pTypeSymbol = NULL;
    if (pSymbol != NULL && pSession != NULL)
    {
        DWORD symbolTypeId;
        pSymbol->get_typeId(&symbolTypeId);
        pSession->symbolById(symbolTypeId, &pTypeSymbol);
    }
    return(pTypeSymbol);
}
```

## <a name="see-also"></a>Vea también
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
