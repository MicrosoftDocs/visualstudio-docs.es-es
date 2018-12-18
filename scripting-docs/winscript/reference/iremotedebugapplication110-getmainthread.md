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
ms.openlocfilehash: 2dc420f3c59a59373c6e3a2be9e7254eea451585
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729295"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Devuelve el subproceso principal para los hosts que llaman a [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), en caso contrario, devuelve E_FAIL.  
  
> [!IMPORTANT]
>  [IRemoteDebugApplication (interfaz)](../../winscript/reference/iremotedebugapplication-interface.md) se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
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