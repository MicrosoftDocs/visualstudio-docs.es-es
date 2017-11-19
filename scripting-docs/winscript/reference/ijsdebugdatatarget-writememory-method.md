---
title: "Ijsdebugdatatarget:: WriteMemory (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed562c1cbdd645da6cca87e45f272c25f8bc0d4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory (Método)
Lee la memoria del proceso de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `address`  
 [in] La dirección base del que se va a escribir en la memoria del proceso de destino.  
  
 `pMemory`  
 [in] Los datos se escriban en el espacio de direcciones del proceso especificado.  
  
 `size`  
 [in] El número de bytes que se va a escribir en el proceso.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Antes de que ocurra la transferencia de datos, el sistema comprueba que todos los datos en la memoria del tamaño especificado y la dirección base es accesible para el acceso de escritura, y si no es accesible, la función genera un error E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)