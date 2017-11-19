---
title: IRemoteDebugApplicationThread::GetState | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationThread.GetState
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce34fa73f97b92d08193c697e991c9e922ac17ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Obtiene el estado de este subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pState`  
 [out] Combinación de los siguientes indicadores de estado de subproceso:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|Se está ejecutando el subproceso.|  
|THREAD_STATE_SUSPENDED|0x00000002|El subproceso está suspendido.|  
|THREAD_BLOCKED|0x00000004|El subproceso está bloqueado.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|El subproceso está fuera del contenido.|  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método obtiene el estado de este subproceso.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplicationThread (Interfaz)](../../winscript/reference/iremotedebugapplicationthread-interface.md)