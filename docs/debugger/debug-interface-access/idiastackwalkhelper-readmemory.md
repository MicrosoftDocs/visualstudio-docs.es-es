---
title: IDiaStackWalkHelper::readMemory | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 530b6c3f6873724f8a8ca06ea4228b017de281f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831811"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Lee un bloque de datos de imagen del archivo ejecutable en la memoria.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT readMemory( 
   enum MemoryTypeEnum type,
   ULONGLONG           va,
   DWORD               cbData,
   DWORD*              pcbData,
   BYTE*               pbData
);
```

#### <a name="parameters"></a>Parámetros
 `type`

[in] Un valor de la [MemoryTypeEnum (enumeración)](../../debugger/debug-interface-access/memorytypeenum.md) enumeración que especifica el tipo de memoria para leer.

 va

[in] Dirección virtual en la imagen desde el que se va a comenzar la lectura.

 `cbData`

[in] El tamaño del búfer de datos en bytes.

 `pcbData`

[out] Devuelve el número de bytes leídos realmente. Si `pbData` es `NULL`, este es el número total de bytes de datos disponibles.

 `pbData`

[in, out] Un búfer que se rellena con la memoria de lectura.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [Enumeración MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)