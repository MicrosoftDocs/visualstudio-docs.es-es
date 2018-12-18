---
title: IRemoteDebugApplicationEvents::OnDestroyThread | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnDestroyThread
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnDestroyThread
ms.assetid: 7c716ccc-7b82-41b2-9a16-d0366999dee8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af2d671a6c93cde39c2e3e644243d666e1cd5d46
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728425"
---
# <a name="iremotedebugapplicationeventsondestroythread"></a>IRemoteDebugApplicationEvents::OnDestroyThread
Controla un evento destruido por el subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT OnDestroyThread(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `prdat`  
 [in] El subproceso que se ha destruido.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método controla el evento destruido por el subproceso.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplicationEvents (Interfaz)](../../winscript/reference/iremotedebugapplicationevents-interface.md)