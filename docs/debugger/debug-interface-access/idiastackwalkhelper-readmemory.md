---
title: 'IDiaStackWalkHelper:: ReadMemory (| Microsoft Docs'
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
ms.openlocfilehash: 57afd033b2d969a4ed57dc713b2c4266e0ead632
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741360"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
Lee un bloque de datos de la imagen del archivo ejecutable en la memoria.

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

de Un valor de la enumeración de [enumeración memorytypeenum (](../../debugger/debug-interface-access/memorytypeenum.md) que especifica el tipo de memoria que se va a leer.

 va

de Dirección virtual de la imagen de la que se va a empezar a leer.

 `cbData`

de Tamaño del búfer de datos en bytes.

 `pcbData`

enuncia Devuelve el número de bytes leídos realmente. Si `pbData` es `NULL`, es el número total de bytes de datos disponibles.

 `pbData`

[in, out] Búfer que se rellena con la lectura de memoria.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [Enumeración MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)