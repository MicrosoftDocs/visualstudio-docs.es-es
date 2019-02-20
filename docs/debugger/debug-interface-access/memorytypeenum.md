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
ms.openlocfilehash: 6e0f0973c0491cd65c2d03be785bb03b8c2f31df
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227425"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Especifica el tipo de memoria para tener acceso.

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
`MemTypeCode`  
Accesos a memoria sólo el código.

`MemTypeData`  
Memoria de pila o datos de accesos.

`MemTypeStack`  
Tiene acceso a la pila sólo memoria.

`MemTypeAny`  
Tiene acceso a cualquier tipo de memoria.

## <a name="remarks"></a>Comentarios
Los valores de esta enumeración se pasan a la [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) método para limitar el acceso a diferentes tipos de memoria.

## <a name="requirements"></a>Requisitos
Encabezado: cvconst.h

## <a name="see-also"></a>Vea también
[Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
