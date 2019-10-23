---
title: IDiaStackFrame::get_localsBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_localsBase method
ms.assetid: eb0bd73e-d92d-468e-a0b1-fbc279919f54
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ae3f83469e14e826802ca82d3d58686a340d9e0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741658"
---
# <a name="idiastackframeget_localsbase"></a>IDiaStackFrame::get_localsBase
Recupera la dirección base de las variables locales para el marco.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_localsBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve la dirección base de las variables locales.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite la propiedad. De lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)