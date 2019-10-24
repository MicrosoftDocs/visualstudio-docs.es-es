---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0710ec5cdfcfcb59407d18b43b885603f017fdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738631"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Especifica el tipo de memoria a la que se va a obtener acceso.

## <a name="syntax"></a>Sintaxis

```C++
enum MemoryTypeEnum {
    MemTypeCode,
    MemTypeData,
    MemTypeStack,
    MemTypeAny = -1
};
```

#### <a name="parameters"></a>Parámetros
`MemTypeCode` solo tiene acceso a la memoria de código.

`MemTypeData` tiene acceso a los datos o a la memoria de la pila.

`MemTypeStack` solo tiene acceso a la memoria de la pila.

`MemTypeAny` tiene acceso a cualquier tipo de memoria.

## <a name="remarks"></a>Comentarios
Los valores de esta enumeración se pasan al método [IDiaStackWalkHelper:: ReadMemory (](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) para limitar el acceso a diferentes tipos de memoria.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst. h

## <a name="see-also"></a>Vea también
- [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
