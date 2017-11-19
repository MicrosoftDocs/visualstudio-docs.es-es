---
title: "Ijsdebugdatatarget:: ReadMemory (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1b67b33e17761a675d6ced9e175b4206ede2e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory (Método)
Lee la memoria del proceso de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 [in] Indicadores que controlan el comportamiento de ReadMemory.  
  
 `pBuffer`  
 [out] Un búfer que recibe el contenido desde el espacio de direcciones del proceso de destino. En caso de error, el contenido de este búfer no está especificado.  
  
 `size`  
 [in] El número de bytes que se leen desde el proceso.  
  
 `pBytesRead`  
 [out] Indica el número de bytes leídos desde el proceso de destino. Si JsDebugAllowPartialRead está desactivada, se ejecuta correctamente este valor siempre será exactamente igual que el tamaño de entrada. Si se especifica JsDebugAllowPartialRead, se ejecuta correctamente, este valor será mayor que cero.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve S_OK en ejecución satisfactoria y códigos de error se usa para los errores. Devuelve E_JsDEBUG_INVALID_MEMORY_ADDRESS si la dirección no es válida. Para obtener más información, vea JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)