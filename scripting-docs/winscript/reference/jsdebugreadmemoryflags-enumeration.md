---
title: Enumeración JsDebugReadMemoryFlags | Documentos de Microsoft
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
ms.openlocfilehash: c908fdbf17b13b84355dff208b7f3106bfc72087
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156416"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>Enumeración JsDebugReadMemoryFlags
Marcas para especificar el comportamiento al leer la memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Indica que el llamador desea que la operación de lectura se realice correctamente si solo parte de la memoria de lectura se ha realizado correctamente. Si se establece, solo se produce un error E_JsDEBUG_INVALID_MEMORY_ADDRESS si 'Direcciones' no es válido. Si esta marca está desactivada, se generará un error E_JsDEBUG_INVALID_MEMORY_ADDRESS si cualquier parte de la memoria solicitada era ilegible.|  
|`None`|Indica que el llamador desea el comportamiento predeterminado para ReadMemory.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia de interfaces de Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)