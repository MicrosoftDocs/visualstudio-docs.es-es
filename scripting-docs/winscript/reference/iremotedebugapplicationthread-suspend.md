---
title: IRemoteDebugApplicationThread::Suspend | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.Suspend
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::Suspend
ms.assetid: fd5cc874-2970-4092-b1cd-e638775b0e20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ba783b1f6f275eafe05872ad3755b425b65407e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152686"
---
# <a name="iremotedebugapplicationthreadsuspend"></a>IRemoteDebugApplicationThread::Suspend
Suspende el subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Suspend(  
   DWORD*  pdwCount  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwCount`  
 [out] El recuento de suspensión del subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando este método suspende el subproceso, incrementa el recuento de suspensión.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplicationThread (Interfaz)](../../winscript/reference/iremotedebugapplicationthread-interface.md)