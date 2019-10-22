---
title: Enumeración JsDebugReadMemoryFlags | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a1757678f20a01221ae46e1535d3190cd463d724
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571704"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Enumeración JsDebugReadMemoryFlags
Marcas para especificar el comportamiento al leer la memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="values"></a>Valores  
  
|Name|Descripción|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Indica que el llamador desea que la operación de lectura se realice correctamente si solo una parte de la memoria se leyó correctamente. Si se establece, solo se generará un error E_JsDEBUG_INVALID_MEMORY_ADDRESS si ' address ' no es válido. Si esta marca está desactivada, se producirá un error E_JsDEBUG_INVALID_MEMORY_ADDRESS si alguna parte de la memoria solicitada no se puede leer.|  
|`None`|Indica que el llamador desea el comportamiento predeterminado de ReadMemory (.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)