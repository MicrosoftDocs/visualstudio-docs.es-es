---
title: IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dde2f111e468b8ccf6c1d91440f06d3e7048a0f6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742852"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
Lee `ULONGLONG` valores de un conjunto de propiedades.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT ReadULONGLONG ( 
   PROPID     id,
   ULONGLONG* pValue
);
```

#### <a name="parameters"></a>Parámetros
 `id`

de Identificador de la propiedad que se va a leer (`PROPID` se define en WTypes. h como `ULONG`).

 `pValue`

enuncia Devuelve el valor de propiedad.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_INVALIDARG` si la propiedad no es de tipo `ULONGLONG`.

## <a name="remarks"></a>Comentarios
 Windows define un `ULONGLONG` como un entero de 64 bits sin signo.

## <a name="see-also"></a>Vea también
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)