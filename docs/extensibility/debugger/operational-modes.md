---
title: Modos operativos | Microsoft Docs
description: Obtenga información sobre los tres modos en los que puede funcionar el IDE, que son el modo de diseño, el modo de ejecución y el modo de interrupción.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 559df92545f4c14eb0575e7ef758e73028349b76
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899113"
---
# <a name="operational-modes"></a>Modos operativos
Hay tres modos en los que el IDE puede funcionar, como se muestra a continuación:

- [Modo de diseño](#vsconoperationalmodesanchor1)

- [Modo de ejecución](#vsconoperationalmodesanchor2)

- [Modo de interrupción](#vsconoperationalmodesanchor3)

  La forma en que el motor de depuración personalizado (DE) realiza la transición entre estos modos es una decisión de implementación que requiere que esté familiarizado con los mecanismos de transición. El DE puede o no implementar directamente estos modos. Estos modos son realmente modos de paquete de depuración que cambian en función de la acción del usuario o de los eventos del DE. Por ejemplo, la transición del modo de ejecución al modo de interrupción se produce mediante un evento de detención desde el DE. La transición de break al modo de ejecución o al modo de paso se realiza mediante el usuario que realiza operaciones como Step o Execute. Para obtener más información sobre las transiciones de DE, vea [Control de ejecución.](../../extensibility/debugger/control-of-execution.md)

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Modo de diseño
 El modo de diseño es el estado de no ejecución Visual Studio depuración, durante el cual puede establecer características de depuración en la aplicación.

 Solo se usan algunas características de depuración durante el modo de diseño. Un desarrollador puede optar por establecer puntos de interrupción o crear expresiones de reloj. El DE nunca se carga ni se llama mientras el IDE está en modo de diseño. La interacción con el DE tiene lugar solo durante los modos de ejecución y interrupción.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Modo de ejecución
 El modo de ejecución se produce cuando un programa se ejecuta en una sesión de depuración en el IDE. La aplicación se ejecuta hasta la finalización, hasta que se alcanzará un punto de interrupción o hasta que se produce una excepción. Cuando la aplicación se ejecuta hasta la finalización, de pasa al modo de diseño. Cuando se encuentra un punto de interrupción o se produce una excepción, el DE pasa al modo de interrupción.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Modo de interrupción
 El modo de interrupción se produce cuando se suspende la ejecución del programa de depuración. El modo de interrupción ofrece al desarrollador una instantánea de la aplicación en el momento de la interrupción y permite al desarrollador analizar el estado de la aplicación y cambiar cómo se ejecutará la aplicación. El desarrollador puede ver y editar código, examinar o modificar datos, reiniciar la aplicación, finalizar la ejecución o continuar la ejecución desde el mismo punto.

 El modo de interrupción se introduce cuando el DE envía un evento de detención sincrónico. Los eventos de detención sincrónicos, también denominados eventos de detención, notifican al administrador de depuración de sesión (SDM) y al IDE que la aplicación que se está depurando ha dejado de ejecutar código. Las [interfaces IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) [e IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) son ejemplos de eventos de detención.

 La detención de eventos continúa mediante una llamada a uno de los métodos siguientes, que transición del depurador del modo de interrupción al modo de ejecución o paso:

- [Ejecutar](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Continuar](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Modo paso a paso
 El modo paso a paso se produce cuando el programa se guía a la siguiente línea de código, o dentro o fuera de una función. Se ejecuta un paso mediante una llamada al método [Step](../../extensibility/debugger/reference/idebugprocess3-step.md). Este método requiere `DWORD` que especifique las enumeraciones [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) y [STEPKIND](../../extensibility/debugger/reference/stepkind.md) como parámetros de entrada.

 Cuando el programa pasa correctamente a la siguiente línea de código o a una función, o se ejecuta hasta el cursor o a un punto de interrupción establecido, el DE realiza automáticamente la transición al modo de interrupción.

## <a name="see-also"></a>Consulta también
- [Control de la ejecución](../../extensibility/debugger/control-of-execution.md)
