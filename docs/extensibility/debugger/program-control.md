---
title: Control de programa | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb69afe513010a7da4b4a85669bbc5f145f8dbc5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="program-control"></a>Control de programas
En Visual Studio depuración todos de la versión siguiente y continuar rutinas se producen en el nivel de programa:  
  
-   Establecer la siguiente instrucción, es decir, si se establece el equipo en la siguiente instrucción que se ejecuta en un entorno determinado fotograma  
  
-   Es decir, ejecutar, continuar salir del modo de ejecución paso a paso  
  
-   Ejecución paso a paso a la siguiente instrucción  
  
-   Continuar con el modo de ejecución paso a paso actual  
  
-   La suspensión de los subprocesos que contiene el programa  
  
-   Reanudar los subprocesos que contiene el programa  
  
> [!NOTE]
>  Ver la pila de llamadas se implementa en el nivel de subproceso. Para enumerar la información de marco al ver la pila de llamadas para un subproceso, debe implementar todos los métodos de la [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaz.  
  
## <a name="methods-of-program-control"></a>Métodos de Control del programa  
 La tabla siguiente muestran los métodos de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que debe implementarse para un motor de depuración mínimamente funcional (Alemania) y el control de la ejecución.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continúa ejecutando todos los subprocesos que contiene un programa desde un estado de detención. Necesaria para el control de ejecución.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continúa ejecutando todos los subprocesos que contiene un programa desde un estado de detención. Necesaria para el control de ejecución.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Realiza un paso en el subproceso especificado. Sigue ejecutándose de todos los demás subprocesos que contiene el programa. Necesaria para el control de ejecución.|  
  
 Para los programas multiproceso, debe implementar también el [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) método y todos los métodos de la [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)