---
title: Modos operativos | Microsoft Docs
description: Obtenga información sobre los tres modos en los que el IDE puede operar, que son el modo de diseño, el modo de ejecución y el modo de interrupción.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0187a02dd14966ee9354d8865991531f1d66ae6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884902"
---
# <a name="operational-modes"></a>Modos operativos
Hay tres modos en los que el IDE puede funcionar, como se indica a continuación:

- [Modo de diseño](#vsconoperationalmodesanchor1)

- [Modo de ejecución](#vsconoperationalmodesanchor2)

- [Modo de interrupción](#vsconoperationalmodesanchor3)

  Cómo su motor DE depuración personalizado (DE) realiza las transiciones entre estos modos es una decisión de implementación que requiere que esté familiarizado con los mecanismos de transición. DE puede o no implementar directamente estos modos. Estos modos son realmente depurar los modos de paquete que cambian en función de la acción del usuario o los eventos del DE. Por ejemplo, la transición del modo de ejecución al modo de interrupción se realiza mediante un evento de detención del de. La transición del modo de interrupción al modo de ejecución o al modo de paso se ha realizado por el usuario que realiza operaciones como el paso o la ejecución. Para obtener más información acerca DE las transiciones, vea [control de la ejecución](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Modo de diseño
 El modo de diseño es el estado no en ejecución de depuración de Visual Studio, durante el cual puede establecer características de depuración en la aplicación.

 Durante el modo de diseño, solo se usan algunas características de depuración. Un desarrollador puede optar por establecer puntos de interrupción o crear expresiones de inspección. La DE no se carga nunca ni se llama mientras el IDE está en modo de diseño. La interacción con el DE tiene lugar solo durante los modos DE ejecución y DE interrupción.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Modo de ejecución
 El modo de ejecución se produce cuando un programa se ejecuta en una sesión de depuración en el IDE. La aplicación se ejecuta hasta la finalización, hasta que se alcanza un punto de interrupción o hasta que se produce una excepción. Cuando la aplicación se ejecuta hasta su finalización, el DE pasa al modo DE diseño. Cuando se alcanza un punto de interrupción o se produce una excepción, el DE pasa al modo DE interrupción.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Modo de interrupción
 El modo de interrupción se produce cuando se suspende la ejecución del programa de depuración. El modo de interrupción ofrece al desarrollador una instantánea de la aplicación en el momento de la interrupción y permite al desarrollador analizar el estado de la aplicación y cambiar el modo en que se ejecutará la aplicación. El desarrollador puede ver y editar el código, examinar o modificar datos, reiniciar la aplicación, finalizar la ejecución o continuar la ejecución desde el mismo punto.

 El modo DE interrupción se especifica cuando el DE envía un evento DE detención sincrónica. Los eventos de detención sincrónica, también denominados detener eventos, notifican al administrador de depuración de la sesión (SDM) y al IDE que la aplicación que se está depurando ha dejado de ejecutar código. Las interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) y [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) son ejemplos de detención de eventos.

 La detención de eventos se continúa mediante una llamada a uno de los métodos siguientes, que transfieren el depurador del modo de interrupción al modo de ejecución o paso:

- [Ejecutar](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Continuar](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Modo de paso
 El modo de paso se produce cuando el programa se ejecuta en la siguiente línea de código, o en, sobre o fuera de una función. Un paso se ejecuta llamando al [paso](../../extensibility/debugger/reference/idebugprocess3-step.md)del método. Este método requiere `DWORD` que especifique las enumeraciones [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) y [STEPKIND](../../extensibility/debugger/reference/stepkind.md) como parámetros de entrada.

 Cuando el programa se recorre correctamente en la siguiente línea de código o en una función, o se ejecuta hasta el cursor o hasta un punto de interrupción establecido, el DE realiza la transición automáticamente al modo DE interrupción.

## <a name="see-also"></a>Vea también
- [Control de la ejecución](../../extensibility/debugger/control-of-execution.md)
