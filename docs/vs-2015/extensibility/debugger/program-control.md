---
title: Control del programa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8102bc488d5c74f751fb93584016aa6904fbe2d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842682"
---
# <a name="program-control"></a>Control de programas
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En la depuración de Visual Studio, todas las siguientes rutinas de paso y continuo se producen en el nivel de programa:  
  
- Establecer la siguiente instrucción, es decir, establecer el equipo en la siguiente instrucción que se va a ejecutar en un entorno de fotogramas determinado  
  
- Ejecutar, es decir, continuar saliendo del modo de ejecución  
  
- Avanzar a la siguiente instrucción  
  
- Continuar con el modo de ejecución actual  
  
- Suspender los subprocesos que contiene el programa  
  
- Reanudar los subprocesos incluidos en el programa  
  
> [!NOTE]
> La visualización de la pila de llamadas se implementa en el nivel de subproceso. Para enumerar la información del marco al ver la pila de llamadas de un subproceso, debe implementar todos los métodos de la interfaz [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) .  
  
## <a name="methods-of-program-control"></a>Métodos de control de programas  
 En la tabla siguiente se muestran los métodos de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que se deben implementar para un motor de depuración (de) y un control de ejecución mínimos funcionalmente.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continúa la ejecución de todos los subprocesos que contiene un programa desde un estado detenido. Necesario para el control de ejecución.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continúa la ejecución de todos los subprocesos que contiene un programa desde un estado detenido. Necesario para el control de ejecución.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Realiza un paso en el subproceso especificado. Continúa ejecutando todos los demás subprocesos que contiene el programa. Necesario para el control de ejecución.|  
  
 En el caso de los programas multiproceso, también debe implementar el método [IDebugProgram2:: enumthreads (](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) y todos los métodos de la interfaz [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) .  
  
## <a name="see-also"></a>Consulte también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
