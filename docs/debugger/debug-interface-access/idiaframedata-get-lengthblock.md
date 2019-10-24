---
title: IDiaFrameData::get_lengthBlock | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthBlock method
ms.assetid: 2e54deb7-7744-428e-913c-1d47a2aa89b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da5b175c7e51e5ee8aaab29788f71219091d26f0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743587"
---
# <a name="idiaframedataget_lengthblock"></a>IDiaFrameData::get_lengthBlock
Recupera la longitud, en bytes, del bloque de código descrito por el marco.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_lengthBlock ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

enuncia Devuelve el número de bytes de código del marco.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 El valor devuelto por este método se utiliza normalmente en la interpretación de una cadena de programa (vea el método [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) para ver la definición de una cadena de programa).

## <a name="see-also"></a>Vea también
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)