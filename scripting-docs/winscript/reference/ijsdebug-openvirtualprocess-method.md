---
title: 'IJsDebug:: Openvirtualprocess ((método) | Microsoft Docs'
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
ms.openlocfilehash: 3de39beb28a68ec3b8e0d76b17a7e914a464ecfe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577745"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess (Método)
Método de generador que se usa para crear un nuevo objeto de proceso virtual.  
  
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
 de Identificador del proceso al que adjuntar el depurador.  
  
 `runtimeJsBaseAddress`  
 de Dirección base en la que el tiempo de ejecución de JavaScript se ha cargado en el proceso de destino.  
  
 `pDataTarget`  
 de Interfaz proporcionada por el depurador para consultar el estado del proceso.  
  
 `ppProcess`  
 enuncia Nuevo objeto de proceso de depuración  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="remarks"></a>Comentarios  
 Devuelve E_JsDEBUG_MISMATCHED_RUNTIME si Jscript9diag y Jscript9 no coinciden.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebug (Interfaz)](../../winscript/reference/ijsdebug-interface.md)