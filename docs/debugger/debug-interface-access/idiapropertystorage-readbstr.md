---
title: IDiaPropertyStorage::ReadBSTR | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef0b5bac11a1bf3da7e8081f7ae24b6a7a6f1a71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742917"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Lee `BSTR` valores de un conjunto de propiedades.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Parámetros
 `id`

de Identificador de la propiedad que se va a leer (`PROPID` se define en WTypes. h como `ULONG`).

 `pValue`

enuncia Devuelve el valor de propiedad.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. Devuelve `E_INVALIDARG` si la propiedad no es de tipo `BSTR`.

## <a name="remarks"></a>Comentarios
 Windows define un `BSTR` como una cadena de caracteres anchos terminada en cero.

## <a name="see-also"></a>Vea también
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)