---
title: IDebugThreadCall::ThreadCallHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugThreadCall.ThreadCallHandler
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugThreadCall::ThreadCallHandler
ms.assetid: c6d5d9db-bfed-44ec-90bc-46637f7de0ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1802cdcdabe2ae462960378d0e869838cdaa6e5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145296"
---
# <a name="idebugthreadcallthreadcallhandler"></a>IDebugThreadCall::ThreadCallHandler
Controla las llamadas a ejecutar código en otro subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT ThreadCallHandler(  
   DWORD_PTR  dwParam1,  
   DWORD_PTR  dwParam2,  
   DWORD_PTR  dwParam3  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwParam1`  
 [in] El primer parámetro.  
  
 `dwParam2`  
 [in] El segundo parámetro.  
  
 `dwParam3`  
 [in] El tercer parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método controla las llamadas a ejecutar código en el subproceso del depurador.  
  
## <a name="see-also"></a>Vea también  
 [IDebugThreadCall (interfaz)](../../winscript/reference/idebugthreadcall-interface.md)   
 [IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)   
 [IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)