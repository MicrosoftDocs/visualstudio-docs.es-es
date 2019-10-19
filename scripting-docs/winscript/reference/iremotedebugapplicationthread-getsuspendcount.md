---
title: 'Iremotedebugapplicationthread (:: GetSuspendCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetSuspendCount
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetSuspendCount
ms.assetid: 37f9936c-fd7c-412d-9a7f-628ca3a90438
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53370d3489f5bb3c8dc8dfe9349ccc32ca923f05
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575236"
---
# <a name="iremotedebugapplicationthreadgetsuspendcount"></a>IRemoteDebugApplicationThread::GetSuspendCount
Devuelve el recuento de suspensión del subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetSuspendCount(  
   DWORD*  pdwCount  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdwCount`  
 enuncia Recuento de suspensiones del subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el recuento de suspensión del subproceso.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplicationThread (Interfaz)](../../winscript/reference/iremotedebugapplicationthread-interface.md)