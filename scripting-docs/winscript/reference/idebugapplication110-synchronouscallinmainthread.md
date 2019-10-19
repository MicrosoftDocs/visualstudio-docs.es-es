---
title: 'Idebugapplication110 (:: SynchronousCallInMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::SynchronousCallInMainThread
ms.assetid: 57475ae5-1520-45ef-800d-ccfc6235a5d1
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db2b94d51cc5c9a65355aae7405fb162f564e0cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573654"
---
# <a name="idebugapplication110synchronouscallinmainthread"></a>IDebugApplication110::SynchronousCallInMainThread
Realiza una llamada sincrónica en el subproceso principal.  
  
> [!IMPORTANT]
> La [interfaz idebugapplication110 (](../../winscript/reference/idebugapplication110-interface.md) se implementa mediante PDM v 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pptc`  
 Objeto de [interfaz idebugthreadcall (](../../winscript/reference/idebugthreadcall-interface.md) que se va a llamar.  
  
 `dwParam1`  
 Primer parámetro de la llamada.  
  
 `dwParam1`  
 Primer parámetro de la llamada.  
  
 `dwParam2`  
 Segundo parámetro de la llamada.  
  
 `dwParam3`  
 Tercer parámetro de la llamada.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication110 (Interfaz)](../../winscript/reference/idebugapplication110-interface.md)