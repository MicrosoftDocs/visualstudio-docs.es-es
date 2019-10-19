---
title: 'Idebugapplicationthread (:: SynchronousCallIntoThread | Microsoft Docs'
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
ms.openlocfilehash: d545782f8103d10b38f3eb0d2f149c4ef3b9dc95
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574497"
---
# <a name="idebugapplicationthreadsynchronouscallintothread"></a>IDebugApplicationThread::SynchronousCallIntoThread
Proporciona un mecanismo para que el llamador ejecute código en el subproceso de la aplicación.  
  
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
 de Objeto al que se va a llamar.  
  
 `dwParam1`  
 de Primer parámetro que se va a pasar al método `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam2`  
 de Segundo parámetro que se va a pasar al método `IDebugThreadCall::ThreadCallHandler`.  
  
 `dwParam3`  
 de Tercer parámetro que se va a pasar al método `IDebugThreadCall::ThreadCallHandler`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método proporciona un mecanismo para que el llamador ejecute código en el subproceso del depurador. Los motores y hosts de lenguaje suelen usar este método para implementar objetos de subprocesos libres en las implementaciones de un solo subproceso.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugapplicationthread (](../../winscript/reference/idebugapplicationthread-interface.md)  
 [IDebugThreadCall (Interfaz)](../../winscript/reference/idebugthreadcall-interface.md)