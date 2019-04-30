---
title: IRemoteDebugApplication110::GetMainThread | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 8a4b51d87f89d77bebf065ce5f52a297ada333d3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63383506"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
Devuelve el subproceso principal para los hosts que llaman a [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439), en caso contrario, devuelve E_FAIL.  
  
> [!IMPORTANT]
> [IRemoteDebugApplication (interfaz)](../../winscript/reference/iremotedebugapplication-interface.md) es implementada por PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
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