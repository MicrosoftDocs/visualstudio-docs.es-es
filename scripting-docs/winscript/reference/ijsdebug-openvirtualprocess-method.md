---
title: Método Ijsdebug | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97a055bf1550d74dc6b86d93ffdb9ca406afb43d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151952"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess (Método)
Método de generador usado para crear un nuevo objeto de proceso virtual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `processId`  
 [in] Id. de proceso para asociar al depurador.  
  
 `runtimeJsBaseAddress`  
 [in] La dirección base en el que se ha cargado el runtime de JavaScript en el proceso de destino.  
  
 `pDataTarget`  
 [in] Interfaz proporcionado para consultar el estado del proceso del depurador.  
  
 `ppProcess`  
 [out] Nuevo objeto de proceso de depuración  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve E_JsDEBUG_MISMATCHED_RUNTIME si no coinciden Jscript9diag y Jscript9.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebug (Interfaz)](../../winscript/reference/ijsdebug-interface.md)