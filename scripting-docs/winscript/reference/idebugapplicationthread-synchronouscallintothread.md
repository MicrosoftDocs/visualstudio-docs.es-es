---
title: IDebugApplicationThread::SynchronousCallIntoThread | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationThread.SynchronousCallIntoThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::SynchronousCallIntoThread
ms.assetid: 8a91157f-dade-418a-ad02-5607ce12c95c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5e25f42b2bce66cf3bb7ab3e69d3711e2526ae1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097063"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Proporciona un mecanismo para que el llamador ejecutar código en el subproceso de la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SynchronousCallIntoThread(  
   IDebugThreadCall*  pstcb,  
   DWORD_PTR          dwParam1,  
   DWORD_PTR          dwParam2,  
   DWORD_PTR          dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstcb`  
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
 Este método proporciona un mecanismo para que el llamador ejecutar código en el subproceso del depurador. Hosts y motores de lenguaje normalmente utilizan este método para implementar objetos de subprocesamiento libre encima de sus implementaciones de subprocesos únicos.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationThread (interfaz)](../../winscript/reference/idebugapplicationthread-interface.md)   
 [IDebugThreadCall (Interfaz)](../../winscript/reference/idebugthreadcall-interface.md)