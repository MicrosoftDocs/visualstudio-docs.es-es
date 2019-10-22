---
title: IDiaStackWalkFrame::readMemory | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82ef0d25e796f9e04ecdcfd0c54a7312b9c9edad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837919"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Lee de la imagen de memoria.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT readMemory ( 
   MemoryTypeEnum type,
   ULONGLONG va,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>Parámetros
 `type`

[in] Uno de los [MemoryTypeEnum (enumeración)](../../debugger/debug-interface-access/memorytypeenum.md) valores de enumeración que especifica el tipo de memoria para tener acceso.

 `va`

[in] Ubicación de dirección virtual de imagen a comenzar la lectura.

 `cbData`

[in] Tamaño del búfer de datos, en bytes.

 `pcbData`

[out] Devuelve el número de bytes devueltos. Si `data` es `NULL`, a continuación, `pcbData` contiene el número total de bytes de datos disponibles.

 `data`

[out] Un búfer que se va a rellenar con datos de la ubicación especificada.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)