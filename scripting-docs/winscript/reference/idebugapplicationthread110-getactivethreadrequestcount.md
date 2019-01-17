---
title: IDebugApplicationThread110::GetActiveThreadRequestCount | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8bd776aedd4df61797419795afb8dcc8afeb9318
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348196"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Devuelve el número de solicitudes de subproceso del subproceso de PDM conmutación mecanismos que se están procesando actualmente. Normalmente, este número es 0 o 1. Sin embargo, el número puede ser mayor si una llamada de subproceso empieza a procesar pero desencadena una llamada sincrónica fuera del subproceso, o en caso contrario, suspende el subproceso y permite volver a procesar las llamadas entrantes (por ejemplo, mediante la activación de un [ IRemoteDebugApplicationEvents (interfaz)](../../winscript/reference/iremotedebugapplicationevents-interface.md) evento, que se emite en el subproceso del depurador).  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 (interfaz)](../../winscript/reference/idebugapplicationthread110-interface.md) es implementada por PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `puiThreadRequests`  
 [out] El número de solicitudes de subproceso.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationThread110 (Interfaz)](../../winscript/reference/idebugapplicationthread110-interface.md)