---
title: IDiaPropertyStorage::ReadDWORD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1764ec83a69dcc5daff267767594473bf690b341
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742908"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
Lee `DWORD` valores de un conjunto de propiedades.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT ReadDWORD ( 
   PROPID id,
   DWORD* pValue
);
```

#### <a name="parameters"></a>Parámetros
 `id`

de Identificador de la propiedad que se va a leer (`PROPID` se define en WTypes. h como `ULONG`).

 `pValue`

enuncia Devuelve el valor de propiedad.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_INVALIDARG` si la propiedad no es de tipo `DWORD`.

## <a name="remarks"></a>Comentarios
 Windows define un `DWORD` como un entero de 32 bits sin signo.

## <a name="see-also"></a>Vea también
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)