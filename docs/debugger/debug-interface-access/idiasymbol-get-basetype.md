---
title: IDiaSymbol::get_baseType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_baseType method
ms.assetid: 5c69a241-a8d3-48ed-8b36-27463a196572
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2844003bf7ec81b256537fe06520dfdff473faa
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227282"
---
# <a name="idiasymbolgetbasetype"></a>IDiaSymbol::get_baseType
Recupera el tipo base para este símbolo<em>.</em>

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_baseType (
    DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
`pRetVal`  
[out] Devuelve un valor de la [BasicType (enumeración)](../../debugger/debug-interface-access/basictype.md) enumeración que especifica el tipo base del símbolo.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
Obteniendo primero el tipo del símbolo de y, a continuación, interrogar que devuelve el tipo para el tipo base se puede determinar el tipo básico para un símbolo. Tenga en cuenta que algunos símbolos pueden no tener un tipo base, por ejemplo, un nombre de la estructura.

## <a name="example"></a>Ejemplo

```C++
IDiaSymbol* pType;
CComPtr<IDiaSymbol> pBaseType;
if (pType->get_type( &pBaseType ) == S_OK)
{
    BasicType btBaseType;
    if (pBaseType->get_baseType((DWORD *)&btBaseType) == S_OK)
    {
        // Do something with basic type.
    }
}
```

## <a name="requirements"></a>Requisitos

|Requisito|Descripción|
|-----------------|-----------------|
|Encabezado:|dia2.h|
|Versión:|SDK de DIA v7.0|

## <a name="see-also"></a>Vea también
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
[Enumeración BasicType](../../debugger/debug-interface-access/basictype.md)  
[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
