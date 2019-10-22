---
title: 'IJsDebugDataTarget:: Freevirtualmemory ((método) | Microsoft Docs'
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
ms.openlocfilehash: 835302249e95c89625c07c6d1ef3d7cbaf2905e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577621"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory (Método)
Libera o anula la confirmación de una región de memoria en el espacio de direcciones virtuales del proceso de destino.  
  
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
 de Dirección dentro del proceso de destino donde se debe liberar la memoria.  
  
 `size`  
 de Número de bytes que se van a anular. Para liberar una región de memoria, este valor debe ser cero.  
  
 `freeType`  
 de Indica el tipo de operación gratuita que se va a realizar. Suele ser MEM_RELEASE (0x8000), que libera la región especificada de páginas. Después de la operación, las páginas se encuentran en el estado libre. En su lugar, se puede usar MEM_DECOMMIT (0x4000) para anular la confirmación de las páginas sin liberarlas.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte la API de VirtualFree de Win32.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugDataTarget (Interfaz)](../../winscript/reference/ijsdebugdatatarget-interface.md)