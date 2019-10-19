---
title: 'Idebugapplicationthread110 (:: IsThreadCallable | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsThreadCallable
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ff81190247454a4471a4150843d3fb0aaed5999
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574467"
---
# <a name="idebugapplicationthread110isthreadcallable"></a>IDebugApplicationThread110::IsThreadCallable
Determina si este subproceso está en un estado que procesará las llamadas realizadas mediante los mecanismos de conmutación de subprocesos de PDM, como SynchronousCallInThread.  
  
> [!IMPORTANT]
> La [interfaz idebugapplicationthread110 (](../../winscript/reference/idebugapplicationthread110-interface.md) se implementa mediante PDM v 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pfIsCallable`  
 [out] `true` si se puede llamar al subproceso, de lo contrario `false`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationThread110 (Interfaz)](../../winscript/reference/idebugapplicationthread110-interface.md)