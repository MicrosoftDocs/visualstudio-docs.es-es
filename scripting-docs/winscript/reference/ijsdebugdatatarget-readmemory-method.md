---
title: 'IJsDebugDataTarget:: ReadMemory ((método) | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84da36433cf3546b34d3e044bb113916c9798117
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572425"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory (Método)
Lee la memoria del proceso de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `address`  
 de Dirección base desde la que se va a leer la memoria del proceso de destino.  
  
 `flags`  
 de Marcas que controlan el comportamiento de ReadMemory (.  
  
 `pBuffer`  
 enuncia Búfer que recibe el contenido del espacio de direcciones del proceso de destino. En caso de error, no se especifica el contenido de este búfer.  
  
 `size`  
 de Número de bytes que se van a leer del proceso.  
  
 `pBytesRead`  
 enuncia Indica el número de bytes leídos del proceso de destino. Si JsDebugAllowPartialRead está desactivado, si se ejecuta correctamente, este valor siempre será exactamente igual al tamaño de entrada. Si se especifica JsDebugAllowPartialRead, si se ejecuta correctamente, este valor será mayor que cero.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve S_OK si se realiza correctamente y los códigos de error se utilizan para cualquier error. Devuelve E_JsDEBUG_INVALID_MEMORY_ADDRESS si la dirección no es válida. Para más información, consulte JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)