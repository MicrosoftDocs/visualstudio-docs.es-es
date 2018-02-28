---
title: IDebugThreadCall (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b2b1b500aec08520166d9092edfa6a58c1df0fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugthreadcall-interface"></a>IDebugThreadCall (Interfaz)
El `IDebugThreadCall` interfaz normalmente se implementa mediante un componente que realiza llamadas a través de subprocesos con el `IDebugThread` implementación proporcionada por el Administrador de depuración (PDM) de proceso de cálculo de referencias.  
  
 Las llamadas PDM la `IDebugThreadCall` interfaz en el subproceso deseado y la `IDebugThreadCall` interfaz envía la llamada a la implementación. El `IDebugThreadCall` interfaz convierte la información de parámetros pasada en los parámetros a la parte superior adecuada.  
  
 La `IDebugThreadCall` interfaz es un objeto de subprocesamiento libre.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `IDebugThreadCall` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Controla las llamadas a ejecutar código en otro subproceso.|