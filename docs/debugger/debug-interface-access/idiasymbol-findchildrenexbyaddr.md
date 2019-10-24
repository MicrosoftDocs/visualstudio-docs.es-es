---
title: IDiaSymbol::findChildrenExByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4dc49d9501e72fb81849943144973574a0d55fef
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741284"
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
Recupera los elementos secundarios del símbolo que son válidos en una dirección especificada.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT findChildrenExByAddr ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parámetros
 `symtag`

de Especifica las etiquetas de símbolos de los elementos secundarios que se van a recuperar, tal como se define en la [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md). Se establece en `SymTagNull` para que se recuperen todos los elementos secundarios.

 `name`

de Especifica el nombre de los elementos secundarios que se van a recuperar. Se establece en `NULL` para que se recuperen todos los elementos secundarios.

 `compareFlags`

de Especifica las opciones de comparación que se aplicarán a la coincidencia de nombres. Los valores de la enumeración [namesearchoptions (](../../debugger/debug-interface-access/namesearchoptions.md) se pueden usar solos o en combinación.

 `address`

de Dirección del símbolo.

 `ppResult`

enuncia Devuelve un objeto [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) que contiene una lista de los símbolos secundarios recuperados.

## <a name="return-value"></a>Valor devuelto
 Devuelve `S_OK` si se encontró al menos un elemento secundario del símbolo, o devuelve `S_FALSE` si no se encontraron elementos secundarios; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Los símbolos locales que se devuelven incluyen información de intervalo en directo.

## <a name="requirements"></a>Requisitos
 Encabezado: Dia2. h

 Biblioteca: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [Enumeración NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)