---
title: IDiaImageData::get_imageBase | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de8c333391530cd86c6fc66a8e6c36ce8cfecd5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829062"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
Recupera la ubicación de memoria donde se debe basar la imagen.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parámetros
 `pRetVal`

[out] Devuelve el valor de base de imagen sugerida.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
 Debido a conflictos de imagen base, una imagen puede reubicarse automáticamente en una ubicación de memoria no utilizada cuando se cargue. Este método devuelve la sugerencia base (ubicación de memoria recomendados) que se almacenó en el módulo en tiempo de compilación.

## <a name="see-also"></a>Vea también
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)