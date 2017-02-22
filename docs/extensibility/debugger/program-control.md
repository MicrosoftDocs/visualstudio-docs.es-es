---
title: "Control de programas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], control de ejecución"
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Control de programas
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En la depuración de Visual Studio, todas las rutinas de paso y de continuación de siguiente aparecen en el nivel del programa:  
  
-   Establecer la siguiente instrucción, es decir, estableciendo el equipo a la siguiente instrucción de ejecutarse en un entorno determinado de cuadro  
  
-   Ejecutar el, es decir, continuando dejando fuera de modo de recorrido  
  
-   Entrada a la siguiente instrucción  
  
-   Continuación con el modo de entrada actual  
  
-   La suspensión de los subprocesos contenido por el programa  
  
-   Reanudación subprocesos contenido por el programa  
  
> [!NOTE]
>  Viendo la pila de llamadas se implementa en el nivel de subproceso.  Para mostrar la información del cuadro para ver la pila de llamadas de un subproceso, debe implementar todos los métodos de la interfaz de [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) .  
  
## métodos de Control de programa  
 La tabla siguiente se muestran los métodos de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que se deben implementar para un control como mínimo funcional de \(DE\) motor y ejecución de depuración.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugProgram2:: Ejecutar](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Sigue ejecutando todos los subprocesos contenidos en un programa de un estado detenido.  Requerido para el control de ejecución.|  
|[IDebugProgram2:: Continuar](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Sigue ejecutando todos los subprocesos contenidos en un programa de un estado detenido.  Requerido para el control de ejecución.|  
|[IDebugProgram2:: paso](../../extensibility/debugger/reference/idebugprogram2-step.md)|Realiza un paso en el subproceso especificado.  Sigue ejecutando los demás contenido por el programa.  Requerido para el control de ejecución.|  
  
 Para los programas multiproceso, también debe implementar el método de [IDebugProgram2:: EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) y todos los métodos de la interfaz de [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) .  
  
## Vea también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)