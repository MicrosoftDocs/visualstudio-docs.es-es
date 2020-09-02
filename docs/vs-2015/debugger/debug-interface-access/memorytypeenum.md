---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ded136da4d601fd7c11a10c21aac0c90864bc0bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158130"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica el tipo de memoria a la que se va a obtener acceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 `MemTypeCode`  
 Solo tiene acceso a la memoria de código.  
  
 `MemTypeData`  
 Obtiene acceso a datos o a la memoria de la pila.  
  
 `MemTypeStack`  
 Solo tiene acceso a la memoria de la pila.  
  
 `MemTypeAny`  
 Obtiene acceso a cualquier tipo de memoria.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración se pasan al método [IDiaStackWalkHelper:: ReadMemory (](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) para limitar el acceso a diferentes tipos de memoria.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst. h  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
