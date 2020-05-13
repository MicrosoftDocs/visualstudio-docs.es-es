---
title: Control de Programas (Program Control) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e77e233050c5ce10aef5053f82c8d26cb984b85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738231"
---
# <a name="program-control"></a>Control del programa
En la depuración de Visual Studio, todas las siguientes rutinas paso a paso y continuas se producen en el nivel de programa:

- Establecer la siguiente instrucción, es decir, establecer el equipo en la siguiente instrucción que se ejecutará en un entorno de marco determinado

- Ejecutando, es decir, continuando saliendo del modo de paso a paso

- Pasar a la siguiente instrucción

- Continuar con el modo de paso actual

- Suspensión de los hilos contenidos por el programa

- Reanudación de los hilos contenidos en el programa

> [!NOTE]
> La visualización de la pila de llamadas se implementa en el nivel de subproceso. Para enumerar la información de marco al ver la pila de llamadas para un subproceso, debe implementar todos los métodos de la [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interfaz.

## <a name="methods-of-program-control"></a>Métodos de control del programa
 En la tabla siguiente se muestran los métodos de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que se deben implementar para un motor de depuración mínimamente funcional (DE) y control de ejecución.

|Método|Descripción|
|------------|-----------------|
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continúa ejecutando todos los subprocesos contenidos en un programa desde un estado detenido. Necesario para el control de ejecución.|
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continúa ejecutando todos los subprocesos contenidos en un programa desde un estado detenido. Necesario para el control de ejecución.|
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Realiza un paso en el subproceso especificado. Continúa ejecutando todos los demás subprocesos contenidos en el programa. Necesario para el control de ejecución.|

 Para los programas multiproceso, también debe implementar el [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) método y todos los métodos de la [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interfaz.

## <a name="see-also"></a>Vea también
- [Control de ejecución y evaluación del estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
