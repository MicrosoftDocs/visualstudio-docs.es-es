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
ms.openlocfilehash: 688652fe3915e1974d5d0e1d04fb1ac075863d8c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743741"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
Recupera un número especificado de tablas en la secuencia de enumeración.

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

de Número de tablas del enumerador que se van a recuperar.

 `rgelt`

enuncia Matriz que se va a rellenar con los objetos [IDiaTable](../../debugger/debug-interface-access/idiatable.md) que representan las tablas deseadas.

 `pceltFetched`

enuncia Devuelve el número de tablas del enumerador recuperado.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no hay más tablas. De lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)