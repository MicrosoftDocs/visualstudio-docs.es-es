---
title: Enumeración JsDebugReadMemoryFlags | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7efb5170bf0314e95b1acded39a897c2236a29ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733715"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Enumeración JsDebugReadMemoryFlags
Marcas para especificar el comportamiento al leer la memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Indica que el llamador desea que lleve a cabo correctamente si sólo parte de la memoria de lectura se ha realizado correctamente la operación de lectura. Si se establece, solo se produce un error E_JsDEBUG_INVALID_MEMORY_ADDRESS si "Dirección" no es válido. Si esta marca está desactivada, se producirá un error de E_JsDEBUG_INVALID_MEMORY_ADDRESS si cualquier parte de la memoria solicitada es ilegible.|  
|`None`|Indica que el llamador desea el comportamiento predeterminado para ReadMemory.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)