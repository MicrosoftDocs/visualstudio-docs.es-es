---
title: IDiaInjectedSource::get_source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 604160cdaf8c1ff28b306106afe34e047768f3c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828425"
---
# <a name="idiainjectedsourcegetsource"></a>IDiaInjectedSource::get_source
Recupera los bytes de código de origen.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_source ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parámetros
 `cbData`

[in] El número de bytes que representa el tamaño del búfer de datos.

 `pcbData`

[out] Devuelve el número de bytes que representa los bytes devueltos. Si `data` es `NULL`, a continuación, `pcbData` es el número total de bytes de datos disponibles.

 `data[]`

[out] Un búfer que se va a rellenar con los bytes de origen.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`. Devuelve `S_FALSE` si no se admite esta propiedad. De lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)