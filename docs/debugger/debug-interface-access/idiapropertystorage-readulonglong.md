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
ms.openlocfilehash: f365578aba73ed94bdcd1d87801fc53030cfecdb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616019"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
Lee `ULONGLONG` valores en un conjunto de propiedades.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT ReadULONGLONG ( 
   PROPID     id,
   ULONGLONG* pValue
);
```

#### <a name="parameters"></a>Parámetros
 `id`

[in] Identificador de la propiedad de lectura (`PROPID` se define en el archivo WTypes.h como un `ULONG`).

 `pValue`

[out] Devuelve el valor de propiedad.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `E_INVALIDARG` si la propiedad no es de tipo `ULONGLONG`.

## <a name="remarks"></a>Comentarios
 Un `ULONGLONG` se define por Windows como un entero de 64 bits sin signo.

## <a name="see-also"></a>Vea también
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)