---
title: IRemoteDebugApplication110::GetMainThread | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20d895f8bd6d4919def00625e9f285afdfe4f866
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349873"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Devuelve el subproceso principal para los hosts que llaman a [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), en caso contrario, devuelve E_FAIL.  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication (interfaz)](../../winscript/reference/iremotedebugapplication-interface.md) es implementada por PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppThread`  
 [out] El método main [IRemoteDebugApplicationThread (interfaz)](../../winscript/reference/iremotedebugapplicationthread-interface.md).  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplication (interfaz)](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 (Interfaz)](../../winscript/reference/iremotedebugapplication110-interface.md)