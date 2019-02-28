---
title: IDiaSegment::get_execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_execute method
ms.assetid: 746cdf8e-9097-415d-ba10-069854153185
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7851d379793ee21562b2993c89442a7fb728ec00
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56601775"
---
# <a name="idiasegmentgetexecute"></a>IDiaSegment::get_execute
Recupera una marca que indica si el segmento es ejecutable.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_execute ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

[out] Devuelve `TRUE` si el segmento está marcado como ejecutable; en caso contrario, devuelve `FALSE`.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)