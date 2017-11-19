---
title: "Ijsdebug:: OpenVirtualProcess (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJSDebug.OpenVirtualProcess
apilocation: jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5acb137337e46a6e84f7d68c9330a3ca847f2e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess (Método)
Método de generador que se usa para crear un nuevo objeto de proceso virtual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `processId`  
 [in] Id. de proceso para adjuntar al depurador.  
  
 `runtimeJsBaseAddress`  
 [in] La dirección base en el que se cargó el runtime de JavaScript en el proceso de destino.  
  
 `pDataTarget`  
 [in] Interfaz proporcionado para consultar el estado del proceso del depurador.  
  
 `ppProcess`  
 [out] Nuevo objeto de proceso de depuración  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve E_JsDEBUG_MISMATCHED_RUNTIME si Jscript9diag y Jscript9 no coinciden.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebug (Interfaz)](../../winscript/reference/ijsdebug-interface.md)