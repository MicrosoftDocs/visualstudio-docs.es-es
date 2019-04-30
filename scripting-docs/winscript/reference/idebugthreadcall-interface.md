---
title: IDebugThreadCall (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89f0fba2f5210cdcf4bb8f17443f948cb9ba1f4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004862"
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall (Interfaz)
El `IDebugThreadCall` interfaz se implementa normalmente mediante un componente que realiza las llamadas entre subprocesos con el `IDebugThread` implementación proporcionada por el Administrador de depuración (PDM) de proceso de serialización.  
  
 Las llamadas PDM el `IDebugThreadCall` interfaz en el subproceso deseado y el `IDebugThreadCall` interfaz envía la llamada a la implementación deseada. El `IDebugThreadCall` interfaz convierte la información de parámetros pasada en los parámetros en la parte superior adecuada.  
  
 El `IDebugThreadCall` interfaz es un objeto de subprocesamiento libre.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `IDebugThreadCall` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Controla las llamadas a ejecutar código en otro subproceso.|