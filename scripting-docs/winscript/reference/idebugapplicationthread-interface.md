---
title: IDebugApplicationThread (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread interface
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 262174d0daecd2c37bafbecee13532ba62e9967f
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347793"
---
# <a name="idebugapplicationthread-interface"></a>IDebugApplicationThread (Interfaz)
Permite que los motores de lenguaje y los hosts para proporcionar sincronización de subprocesos y para mantener la información de estado de depuración específicas de un subproceso. Esta interfaz extiende la `IRemoteDebugApplicationThread` interfaz para proporcionar acceso no remotos para el subproceso.  
  
 Además de los métodos heredados de `IRemoteDebugApplicationThread`, el `IDebugApplicationThread` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Proporciona un mecanismo para que el llamador ejecutar código en el subproceso de la aplicación.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Determina si este subproceso es el subproceso actualmente en ejecución.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Determina si este subproceso es el depurador.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Establece la descripción de este subproceso.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Establece la descripción del estado del subproceso.|