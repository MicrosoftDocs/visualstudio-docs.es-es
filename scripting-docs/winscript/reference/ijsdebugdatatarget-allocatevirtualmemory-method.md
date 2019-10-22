---
title: 'IJsDebugDataTarget:: Allocatevirtualmemory ((método) | Microsoft Docs'
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
ms.openlocfilehash: 30ad8a3eb277823271fbfb4c2e10364b8602775c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577644"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory (Método)
Reserva o confirma una región de memoria en el espacio de direcciones virtuales del proceso de destino.  
  
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
 de La dirección dentro del proceso de destino donde se debe confirmar o reservar la memoria. Este valor suele ser cero, en cuyo caso el sistema elige una dirección.  
  
 `size`  
 de Tamaño de la región de memoria que se va a asignar, en bytes. El sistema se redondeará automáticamente al límite de la página siguiente.  
  
 `allocationType`  
 de Indica el tipo de asignación que se va a realizar. Suele ser MEM_COMMIT &#124; MEM_RESERVE (0x3000), que reserva y confirma una asignación en un solo paso.  
  
 `pageProtection`  
 de La protección de memoria para la región de páginas que se va a asignar. Si las páginas se están confirmando, puede especificar cualquiera de las constantes de protección de memoria (por ejemplo, PAGE_READWRITE, PAGE_EXECUTE).  
  
 `pAllocatedAddress`  
 enuncia Dirección base de la región de páginas asignada.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 La función inicializa la memoria que asigna a cero, a menos que se use MEM_RESET. Para obtener más información, consulte la API de Win32 de VirtualAlloc.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)