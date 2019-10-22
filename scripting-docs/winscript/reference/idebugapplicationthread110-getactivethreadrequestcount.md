---
title: 'Idebugapplicationthread110 (:: GetActiveThreadRequestCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e7f038c1d0958701a14899825a2adb0a11cf604d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574486"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Devuelve el número de solicitudes de subproceso de los mecanismos de conmutación de subprocesos de PDM que se están procesando actualmente. Este número normalmente es 0 o 1. Sin embargo, el número puede ser mayor si una llamada de subproceso comienza el procesamiento, pero desencadena una llamada sincrónica fuera de subproceso o suspende el subproceso, y permite que las llamadas entrantes se procesen de nuevo (por ejemplo, mediante la activación de un [iremotedebugapplicationevents ( ](../../winscript/reference/iremotedebugapplicationevents-interface.md)Evento de interfaz, que se emite en el subproceso del depurador.  
  
> [!IMPORTANT]
> La [interfaz idebugapplicationthread110 (](../../winscript/reference/idebugapplicationthread110-interface.md) se implementa mediante PDM v 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `puiThreadRequests`  
 enuncia Número de solicitudes de subproceso.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplicationThread110 (Interfaz)](../../winscript/reference/idebugapplicationthread110-interface.md)