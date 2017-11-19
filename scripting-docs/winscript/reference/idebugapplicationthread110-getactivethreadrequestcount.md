---
title: IDebugApplicationThread110::GetActiveThreadRequestCount | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb4d19bb77a4380c3c0a04f7e7808b82ca3f6ae4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Devuelve el número de solicitudes de subproceso del subproceso del PDM conmutación mecanismos que se están procesando actualmente. Este número suele ser 0 o 1. Sin embargo, el número puede ser mayor si una llamada de subprocesos empieza a procesar pero desencadena una llamada sincrónica fuera del subproceso, o en caso contrario, suspende el subproceso y permite que las llamadas entrantes al volver a procesar (por ejemplo, mediante la activación de un [ IRemoteDebugApplicationEvents (interfaz)](../../winscript/reference/iremotedebugapplicationevents-interface.md) evento, que se ejecuta en el subproceso del depurador).  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 (interfaz)](../../winscript/reference/idebugapplicationthread110-interface.md) se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `puiThreadRequests`  
 [out] El número de solicitudes de subproceso.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationThread110 (Interfaz)](../../winscript/reference/idebugapplicationthread110-interface.md)