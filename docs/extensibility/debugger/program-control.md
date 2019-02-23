---
title: Control del programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98c63d2eff11997a37d27f71d01403b59f276e2b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679143"
---
# <a name="program-control"></a>Control del programa
En Visual Studio depurando, todos de la versión siguiente y continuar rutinas se producen en el nivel de programa:

-   Establecer la instrucción siguiente, es decir, si se establece el equipo en la siguiente instrucción que se ejecuta en un entorno de marco determinado

-   Es decir, ejecutar, continúe salir del modo de ejecución paso a paso

-   Ejecución paso a paso a la siguiente instrucción

-   Continuando con el modo de ejecución paso a paso actual

-   Suspender los subprocesos contenidos en el programa

-   Reanudar los subprocesos contenidos en el programa

> [!NOTE]
>  Ver la pila de llamadas se implementa en el nivel de subproceso. Para enumerar la información de marco al ver la pila de llamadas para un subproceso, debe implementar todos los métodos de la [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaz.

## <a name="methods-of-program-control"></a>Métodos de control del programa
 La tabla siguiente muestran los métodos de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que debe implementarse para un motor de depuración mínimamente funcional (DE) y el control de ejecución.

|Método|Descripción|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continúa ejecutándose en todos los subprocesos contenidos en un programa desde un estado detenido. Se requiere para el control de ejecución.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continúa ejecutándose en todos los subprocesos contenidos en un programa desde un estado detenido. Se requiere para el control de ejecución.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Realiza un paso en el subproceso especificado. Continúa ejecutándose en todos los demás subprocesos contenidos en el programa. Se requiere para el control de ejecución.|

 Los programas multiproceso, también debe implementar la [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) método y todos los métodos de la [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interfaz.

## <a name="see-also"></a>Vea también
- [Evaluación de control y el estado de ejecución](../../extensibility/debugger/execution-control-and-state-evaluation.md)