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
ms.openlocfilehash: b0ffcb6c438150bff82f17a66c3347c300b17d72
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741883"
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

de Identificador único.

`ppSymbol`

enuncia Devuelve un objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el símbolo recuperado.

## <a name="return-value"></a>Valor devuelto
Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
El identificador especificado es un valor único que usa internamente el SDK de DIA para que todos los símbolos sean únicos.

Este método se puede utilizar, por ejemplo, para recuperar el símbolo que representa el tipo de otro símbolo (vea el ejemplo).

## <a name="example"></a>Ejemplo
En este ejemplo se recupera un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el tipo de otro símbolo. En este ejemplo se muestra cómo utilizar el método `symbolById` en la sesión. Un enfoque más sencillo es llamar al método [IDiaSymbol:: GET_TYPE](../../debugger/debug-interface-access/idiasymbol-get-type.md) para recuperar el símbolo de tipo directamente.

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
