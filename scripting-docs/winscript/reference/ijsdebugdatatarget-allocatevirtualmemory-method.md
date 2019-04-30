---
title: Allocatevirtualmemory (método) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c04bf21882ec39054c74f060eaa2c6f65ac0b4d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583072"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory (Método)
Reserva y/o confirma una región de memoria en el espacio de direcciones virtuales del proceso de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 [in] La dirección dentro del proceso de destino donde la memoria debería asignarse o reservada. Normalmente, este valor es cero, en la que el sistema elige una dirección.  
  
 `size`  
 [in] El tamaño de la región de memoria para asignar, en bytes. El sistema redondea automáticamente hasta que el límite de página siguiente.  
  
 `allocationType`  
 [in] Indica el tipo de asignación a realizar. Normalmente es MEM_COMMIT &#124; MEM_RESERVE (0 x 3000) que se reserva y confirma una asignación en un solo paso.  
  
 `pageProtection`  
 [in] La protección de memoria para la región de páginas asignadas. Si las páginas están confirmadas, puede especificar cualquiera de las constantes de protección de memoria (por ejemplo, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 [out] Dirección base de la región de páginas asignada.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 La función inicializa la memoria que asigna a cero, a menos que se utilice mem_reset. Para obtener más información, vea la API VirtualAlloc de Win32.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)