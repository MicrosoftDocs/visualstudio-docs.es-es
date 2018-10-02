---
title: MemoryTypeEnum | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9800f2d51440387dc5a9cd50cfb0a7758e133124
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580953"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [MemoryTypeEnum](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/memorytypeenum).  
  
Especifica el tipo de memoria para tener acceso.  
  
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



