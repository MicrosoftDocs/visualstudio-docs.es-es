---
title: IRemoteDebugApplicationThread::GetApplication | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.GetApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::GetApplication
ms.assetid: 9446c7f9-cfa2-408f-98c5-64f549783de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abe33d75f7e03944eb0a6f533f2955871ddee342
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145153"
---
# <a name="iremotedebugapplicationthreadgetapplication"></a>IRemoteDebugApplicationThread::GetApplication
Devuelve el objeto de aplicación asociado a este subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetApplication(  
   IRemoteDebugApplication**  pprda  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pprda`  
 [out] El objeto de aplicación asociado con este subproceso.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el objeto de aplicación asociado a este subproceso.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplicationThread (Interfaz)](../../winscript/reference/iremotedebugapplicationthread-interface.md)