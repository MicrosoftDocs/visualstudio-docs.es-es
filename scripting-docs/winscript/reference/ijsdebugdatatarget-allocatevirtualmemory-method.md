---
title: "Ijsdebugdatatarget:: Allocatevirtualmemory (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.AllocateVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65b29bbf9a3405bcfab779bd877f798a863538d5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory (Método)
Reserva o confirma una región de memoria en el espacio de direcciones virtuales del proceso de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `address`  
 [in] La dirección dentro del proceso de destino donde la memoria debe ser confirmada o reservada. Normalmente, este valor es cero, en la que el sistema elige una dirección.  
  
 `size`  
 [in] El tamaño de la región de memoria para asignar, en bytes. El sistema automáticamente redondeará al límite de página siguiente.  
  
 `allocationType`  
 [in] Indica el tipo de asignación para realizar. Esto suele ser MEM_COMMIT &#124; MEM_RESERVE (0 x 3000) que se reserva y confirma una asignación en un solo paso.  
  
 `pageProtection`  
 [in] La protección de memoria para la región de páginas que se va a asignar. Si las páginas se confirmarse, puede especificar cualquiera de las constantes de protección de memoria (por ejemplo, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 [out] Dirección base de la región asignada de páginas.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 La función inicializa la memoria que asigna a cero, a menos que se utiliza MEM_RESET. Para obtener más información, vea la API de Win32 VirtualAlloc.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)