---
title: IDiaSymbol::get_oemId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemId method
ms.assetid: c472830f-c3eb-46ab-9498-cd637763d241
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d417b0c75db1b2153e9a43eb2e45f3d9550971d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739599"
---
# <a name="idiasymbolget_oemid"></a>IDiaSymbol::get_oemId
Recupera el valor del identificador del fabricante de equipos originales (OEM) del símbolo.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_oemId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve un valor único que identifica un OEM.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
 Esta propiedad solo se aplica a símbolos con un tipo de [enumeración symtagenum (](../../debugger/debug-interface-access/symtagenum.md) de `SymTagCustomType`.

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumeración SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)