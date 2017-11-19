---
title: "Ijsdebugdatatarget:: FreeVirtualMemory (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b53d7f80227a1c4eb0ef0293093543c09c5a367
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory (Método)
Libera o anula el registro de una región de memoria en el espacio de direcciones virtuales del proceso de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `address`  
 [in] La dirección dentro del proceso de destino donde se debería liberar la memoria.  
  
 `size`  
 [in] Número de bytes que se va a anular. Para liberar una región de memoria, este valor debe ser cero.  
  
 `freeType`  
 [in] Indica el tipo de operación de liberación a realizar. Por lo general, suele ser MEM_RELEASE (0 x 8000), lo que libera la región especificada de páginas. Después de la operación, las páginas están en el estado libre. MEM_DECOMMIT (0 x 4000) puede utilizarse en su lugar para las páginas de anulación de registro sin su liberación.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, vea la API de Win32 VirtualFree.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)