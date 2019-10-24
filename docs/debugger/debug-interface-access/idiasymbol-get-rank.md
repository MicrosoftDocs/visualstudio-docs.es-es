---
title: IDiaSymbol::get_rank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5cff86464a4034ad869cdfe231a88ad128dbf52
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739484"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
Recupera el rango (número de dimensiones) de una matriz multidimensional de FORTRAN.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_rank ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve el número de dimensiones de una matriz multidimensional de FORTRAN.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.

> [!NOTE]
> Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.

## <a name="remarks"></a>Comentarios
 Rank hace referencia al número de dimensiones de una matriz donde la matriz se declara como `myarray[1,2,3]`. Este ejemplo tiene un rango de 3 y 3 dimensiones. Rank no se aplica a C++ , que usa el concepto de una matriz de matrices para cada dimensión (es decir, `myarray[1][2][3]`).

## <a name="see-also"></a>Vea también
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)