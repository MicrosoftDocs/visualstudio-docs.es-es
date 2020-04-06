---
title: Modos de funcionamiento ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027152b2b2fc18b509a687220e5d963ea1b7e721
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738284"
---
# <a name="operational-modes"></a>Modos operativos
Hay tres modos en los que el IDE puede funcionar, de la siguiente manera:

- [Modo de diseño](#vsconoperationalmodesanchor1)

- [Modo de ejecución](#vsconoperationalmodesanchor2)

- [Modo de interrupción](#vsconoperationalmodesanchor3)

  La forma en que las transiciones del motor de depuración personalizado (DE) entre estos modos es una decisión de implementación que requiere que esté familiarizado con los mecanismos de transición. El DE puede o no implementar directamente estos modos. Estos modos son realmente modos de paquete de depuración que cambian en función de la acción del usuario o eventos de la DE. Por ejemplo, la transición del modo de ejecución al modo de interrupción es instigada por un evento de detención de la DE. La transición de interrupción al modo de ejecución o modo de paso es instigada por el usuario que realiza operaciones como Paso o Ejecutar. Para obtener más información acerca de las transiciones DE, vea [Control de ejecución](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a>Modo de diseño
 El modo de diseño es el estado de no ejecución de la depuración de Visual Studio, durante el cual puede establecer características de depuración en la aplicación.

 Solo se utilizan algunas características de depuración durante el modo de diseño. Un desarrollador puede elegir establecer puntos de interrupción o crear expresiones de inspección. El DE nunca se carga o se llama mientras el IDE está en modo de diseño. La interacción con el DE tiene lugar solo durante los modos de ejecución y interrupción.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a>Modo de ejecución
 El modo de ejecución se produce cuando un programa se ejecuta en una sesión de depuración en el IDE. La aplicación se ejecuta hasta la terminación, hasta que se alcanza un punto de interrupción o hasta que se produce una excepción. Cuando la aplicación se ejecuta hasta la terminación, la DE pasa al modo de diseño. Cuando se alcanza un punto de interrupción o se produce una excepción, la DE pasa al modo de interrupción.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a>Modo de interrupción
 El modo de interrupción se produce cuando se suspende la ejecución del programa de depuración. El modo de interrupción ofrece al desarrollador una instantánea de la aplicación en el momento de la interrupción y permite al desarrollador analizar el estado de la aplicación y cambiar la forma en que se ejecutará la aplicación. El desarrollador puede ver y editar código, examinar o modificar datos, reiniciar la aplicación, finalizar la ejecución o continuar la ejecución desde el mismo punto.

 El modo de interrupción se introduce cuando la DE envía un evento de detención sincrónico. Eventos de detención sincrónicos, también denominados detener eventos, notificar al administrador de depuración de sesión (SDM) y el IDE que la aplicación que se está depurando ha dejado de ejecutar código. Las interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) son ejemplos de eventos de detención.

 Los eventos de detención se continúan mediante una llamada a uno de los métodos siguientes, que realizan la transición del depurador del modo de interrupción al modo de ejecución o paso:

- [Ejecutar](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Continuar](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a>Modo paso
 El modo de paso se produce cuando el programa pasa a la siguiente línea de código, o dentro, encima o fuera de una función. Se ejecuta un paso llamando al método [Step](../../extensibility/debugger/reference/idebugprocess3-step.md). Este método `DWORD`requiere s que especifican las enumeraciones [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) y [STEPKIND](../../extensibility/debugger/reference/stepkind.md) como parámetros de entrada.

 Cuando el programa pasa correctamente a la siguiente línea de código o a una función, o se ejecuta en el cursor o a un punto de interrupción establecido, la DE vuelve automáticamente al modo de interrupción.

## <a name="see-also"></a>Vea también
- [Control de ejecución](../../extensibility/debugger/control-of-execution.md)
