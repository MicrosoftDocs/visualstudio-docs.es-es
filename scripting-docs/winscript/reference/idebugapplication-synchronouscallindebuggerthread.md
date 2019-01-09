---
title: IDebugApplication::SynchronousCallInDebuggerThread | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.SynchronousCallInDebuggerThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::SynchronousCallInDebuggerThread
ms.assetid: 9daa1722-f25a-4691-aefc-fd28672fb883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5c2a4d6c23339a396fbc367e68b81bb13c75adc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089952"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Proporciona un mecanismo para que el llamador ejecutar código en el subproceso del depurador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SynchronousCallInDebuggerThread(  
   IDebugThreadCall*  pptc,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pptc`  
 [in] El objeto va a llamar.  
  
 `dwParam1`  
 [in] Primer parámetro para pasar a la `IDebugThreadCall::ThreadCallHandler` método.  
  
 `dwParam2`  
 [in] Segundo parámetro para pasar a la `IDebugThreadCall::ThreadCallHandler` método.  
  
 `dwParam3`  
 [in] Tercer parámetro para pasar a la `IDebugThreadCall::ThreadCallHandler` método.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Hosts y motores de lenguaje normalmente utilizan este método para implementar objetos de subprocesamiento libre encima de sus implementaciones de subprocesos únicos.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication (interfaz)](../../winscript/reference/idebugapplication-interface.md)   
 [IDebugThreadCall (Interfaz)](../../winscript/reference/idebugthreadcall-interface.md)