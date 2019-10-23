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
ms.openlocfilehash: ae1201fca1fc25cce19b40b47d6435d02d80e1b4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741481"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
Lee la memoria de la imagen.

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

de Uno de los valores de enumeración de la [enumeración memorytypeenum (](../../debugger/debug-interface-access/memorytypeenum.md) que especifica el tipo de memoria a la que se va a obtener acceso.

 `va`

de Ubicación de la dirección virtual de la imagen en la que se va a empezar a leer.

 `cbData`

de Tamaño del búfer de datos, en bytes.

 `pcbData`

enuncia Devuelve el número de bytes devueltos. Si se `NULL` `data`, `pcbData` contiene el número total de bytes de datos disponibles.

 `data`

enuncia Búfer que se va a rellenar con los datos de la ubicación especificada.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)