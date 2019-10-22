---
title: 'Idebugapplicationthread110 (:: AsynchronousCallIntoThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 595e73787421b5a5e9ca9407dd174c50451051c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577409"
---
# <a name="idebugapplicationthread110asynchronouscallintothread"></a>IDebugApplicationThread110::AsynchronousCallIntoThread
Realiza una llamada asincrónica en el subproceso principal.  
  
> [!IMPORTANT]
> La [interfaz idebugapplicationthread110 (](../../winscript/reference/idebugapplicationthread110-interface.md) se implementa mediante PDM v 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
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