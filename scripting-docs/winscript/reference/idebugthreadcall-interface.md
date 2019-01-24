---
title: IDebugThreadCall (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a2167538f2251d961dfcad4a873658d9635a612e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346272"
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