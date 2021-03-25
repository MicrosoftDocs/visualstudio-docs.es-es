---
title: Control del programa | Microsoft Docs
description: Obtenga información sobre las rutinas de depuración de Visual Studio que se producen en el nivel de programa, como la ejecución, la ejecución paso a paso, la continuación y la suspensión y reanudación de subprocesos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d2d869094eff3713a3c9e7ec63a8003bb12a018c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094684"
---
# <a name="program-control"></a>Control de programas
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
- [Control de ejecución y evaluación del estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
