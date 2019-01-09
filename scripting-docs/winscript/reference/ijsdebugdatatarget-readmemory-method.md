---
title: Método Ijsdebugdatatarget | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 66d3709dadfc8da2feb7e6845a7aeaa357235d9e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089185"
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
 [in] La dirección base del que se lee de la memoria del proceso de destino.  
  
 `flags`  
 [in] Marcas que controlan el comportamiento de ReadMemory.  
  
 `pBuffer`  
 [out] Un búfer que recibe el contenido del espacio de direcciones del proceso de destino. En caso de error, se especifica el contenido de este búfer.  
  
 `size`  
 [in] El número de bytes que se leen desde el proceso.  
  
 `pBytesRead`  
 [out] Indica el número de bytes leídos en el proceso de destino. Si JsDebugAllowPartialRead está desactivada, si se ejecuta correctamente este valor siempre será exactamente igual que el tamaño de entrada. Si JsDebugAllowPartialRead está especificado, si se ejecuta correctamente, este valor será mayor que cero.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve S_OK éxito y códigos de error se usa para cualquier error. Devuelve E_JsDEBUG_INVALID_MEMORY_ADDRESS si la dirección no es válida. Para obtener más información, vea JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)