---
title: 'Idebugapplication (:: SynchronousCallInDebuggerThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 134717b6ce30c87ccfb4bbb50ffe958717ae757f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574583"
---
# <a name="idebugapplicationsynchronouscallindebuggerthread"></a>IDebugApplication::SynchronousCallInDebuggerThread
Proporciona un mecanismo para que el llamador ejecute código en el subproceso del depurador.  
  
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
 Los motores y hosts de lenguaje suelen usar este método para implementar objetos de subprocesos libres en las implementaciones de un solo subproceso.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz idebugapplication (](../../winscript/reference/idebugapplication-interface.md)  
 [IDebugThreadCall (Interfaz)](../../winscript/reference/idebugthreadcall-interface.md)