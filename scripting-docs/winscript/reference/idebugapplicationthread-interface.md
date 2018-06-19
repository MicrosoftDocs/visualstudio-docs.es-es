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
ms.openlocfilehash: 6e731ba866504c9a3c3c9ad081a90a12b161355d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725955"
---
# <a name="idebugapplicationthread-interface"></a>IDebugApplicationThread (Interfaz)
Permite que los motores de idioma y hosts para proporcionar la sincronización de subprocesos y mantiene información de estado de depuración específicas de un subproceso. Esta interfaz extiende la `IRemoteDebugApplicationThread` interfaz para proporcionar acceso remoto no es para el subproceso.  
  
 Además de los métodos heredados de `IRemoteDebugApplicationThread`, el `IDebugApplicationThread` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Proporciona un mecanismo para que el llamador ejecutar código en el subproceso de la aplicación.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Determina si este subproceso es el subproceso actualmente en ejecución.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Determina si este subproceso es el subproceso del depurador.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Establece la descripción de este subproceso.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Establece la descripción del estado de subproceso.|