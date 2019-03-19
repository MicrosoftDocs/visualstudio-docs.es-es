---
title: IDebugApplication110 (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c040df103bac464e4f440f23674da966063f0ae
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149674"
---
# <a name="idebugapplication110-interface"></a>IDebugApplication110 (Interfaz)
El `IDebugApplication110` interfaz extiende la funcionalidad de la [IDebugApplication (interfaz)](../../winscript/reference/idebugapplication-interface.md). Puede obtener una instancia de esta interfaz llamando a QueryInterface en una implementación de [IDebugApplication (interfaz)](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Esta interfaz se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 La interfaz `IDebugApplication110` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Realiza una llamada sincrónica en el subproceso principal.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Realiza una llamada asincrónica en el subproceso principal.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Espera a que cualquiera de los identificadores especificados que se señalen al tiempo que permite las llamadas entre subprocesos se publicarán en este subproceso. Este método debe llamarse desde el subproceso del depurador.|