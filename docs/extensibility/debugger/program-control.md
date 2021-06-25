---
title: Control de programa | Microsoft Docs
description: Obtenga información sobre las rutinas Visual Studio depuración que se producen en el nivel de programa, como la ejecución, la ejecución paso a paso, la continuación y la suspensión o reanudación de subprocesos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7b2946309c72fbdddf2794c1da1e773e9a529368
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900722"
---
# <a name="program-control"></a>Control de programa
En Visual Studio depuración, todas las siguientes rutinas paso a paso y continuación se producen en el nivel de programa:

- Establecer la siguiente instrucción, es decir, establecer el equipo en la siguiente instrucción que se va a ejecutar en un entorno de marco determinado

- Ejecutar, es decir, seguir saliendo del modo de ejecución paso a paso

- Paso a paso por instrucciones

- Continuar con el modo de ejecución paso a paso actual

- Suspender los subprocesos contenidos en el programa

- Reanudación de los subprocesos contenidos en el programa

> [!NOTE]
> La visualización de la pila de llamadas se implementa en el nivel de subproceso. Para enumerar la información del marco al ver la pila de llamadas de un subproceso, debe implementar todos los métodos de la [interfaz IEnumDebugFrameInfo2.](../../extensibility/debugger/reference/ienumdebugframeinfo2.md)

## <a name="methods-of-program-control"></a>Métodos del control de programa
 En la tabla siguiente se muestran los métodos de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que se deben implementar para un motor de depuración (DE) mínimamente funcional y un control de ejecución.

|Método|Descripción|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continúa ejecutando todos los subprocesos contenidos en un programa desde un estado detenido. Necesario para el control de ejecución.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continúa ejecutando todos los subprocesos contenidos en un programa desde un estado detenido. Necesario para el control de ejecución.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Realiza un paso en el subproceso dado. Continúa ejecutando todos los demás subprocesos incluidos en el programa. Necesario para el control de ejecución.|

 Para los programas multiproceso, también debe implementar el método [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) y todos los métodos de la [interfaz IEnumDebugThreads2.](../../extensibility/debugger/reference/ienumdebugthreads2.md)

## <a name="see-also"></a>Consulta también
- [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
