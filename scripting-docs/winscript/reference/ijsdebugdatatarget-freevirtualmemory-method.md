---
title: FreeVirtualMemory (método) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf450c03d996a47f9dcd00899ddee46b75d6df32
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146310"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory (Método)
Libera y/o anula una región de memoria en el espacio de direcciones virtuales del proceso de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `address`  
 [in] Dirección dentro del proceso de destino donde se debe liberar la memoria.  
  
 `size`  
 [in] Número de bytes a anular. Para liberar una región de memoria, este valor debe ser cero.  
  
 `freeType`  
 [in] Indica el tipo de operación libre a realizar. Esto suele ser MEM_RELEASE (0 x 8000), lo que libera la región especificada de páginas. Después de la operación, las páginas están en el estado libre. MEM_DECOMMIT (0 x 4000) se puede usar en su lugar para anular las páginas sin liberarlas.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, vea la API VirtualFree de Win32.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)