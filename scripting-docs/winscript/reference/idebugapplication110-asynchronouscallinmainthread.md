---
title: IDebugApplication110::AsynchronousCallInMainThread | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::AsynchronousCallInMainThread
ms.assetid: 13b80ff0-4bed-48c1-8031-d4147b51bf6c
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e3f98ff917475f0f0733163862ff20ef56f04bb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344127"
---
# <a name="idebugapplication110asynchronouscallinmainthread"></a>IDebugApplication110::AsynchronousCallInMainThread
Realiza una llamada asincrónica en el subproceso principal.  
  
> [!IMPORTANT]
>  [IDebugApplication110 (interfaz)](../../winscript/reference/idebugapplication110-interface.md) es implementada por PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pptc`  
 El [IDebugThreadCall (interfaz)](../../winscript/reference/idebugthreadcall-interface.md) objeto va a llamar.  
  
 `dwParam1`  
 El primer parámetro de la llamada.  
  
 `dwParam1`  
 El primer parámetro de la llamada.  
  
 `dwParam2`  
 El segundo parámetro de la llamada.  
  
 `dwParam3`  
 El tercer parámetro de la llamada.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication110 (Interfaz)](../../winscript/reference/idebugapplication110-interface.md)