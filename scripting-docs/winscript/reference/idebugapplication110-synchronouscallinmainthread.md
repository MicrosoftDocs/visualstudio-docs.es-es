---
title: IDebugApplication110::SynchronousCallInMainThread | Documentos de Microsoft
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
ms.openlocfilehash: d98f28f441096886c9ef7f26e63d876455a264e7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446369"
---
# <a name="idebugapplication110synchronouscallinmainthread"></a>IDebugApplication110::SynchronousCallInMainThread
Realiza una llamada sincrónica en el subproceso principal.  
  
> [!IMPORTANT]
> [IDebugApplication110 (interfaz)](../../winscript/reference/idebugapplication110-interface.md) es implementada por PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
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