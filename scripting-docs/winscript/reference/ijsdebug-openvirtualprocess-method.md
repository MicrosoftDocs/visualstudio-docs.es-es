---
title: Método Ijsdebug | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: daa5414153ee55a431294afaf7b167ee91839bfc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093995"
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