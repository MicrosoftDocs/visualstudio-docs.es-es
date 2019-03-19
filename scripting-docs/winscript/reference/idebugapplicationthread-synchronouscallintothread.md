---
title: IDebugApplicationThread::SynchronousCallIntoThread | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f0c9b89332b55a180220820e8ffe1e030d37a848
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146713"
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