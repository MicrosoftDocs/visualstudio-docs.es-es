---
title: IDiaEnumTables::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 15a9ebbd3a3993568e4b6496e04661a63290399e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832748"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Recupera un número especificado de las tablas de la secuencia de enumeración.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT Next ( 
   ULONG       celt,
   IDiaTable** rgelt,
   ULONG*      pceltFetched
);
```

#### <a name="parameters"></a>Parámetros
 `celt`

[in] El número de tablas en el enumerador que se va a recuperar.

 `rgelt`

[out] Una matriz que se va a rellenar con el [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objetos que representan las tablas que desee.

 `pceltFetched`

[out] Devuelve el número de tablas en el enumerador capturado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay ninguna tabla más. De lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)