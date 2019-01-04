---
title: Modos de funcionamiento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 158eca797c13ca7889ea4d7cf2e5d811783e997e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923684"
---
# <a name="operational-modes"></a>Modos de funcionamiento
Hay tres modos en que puede funcionar el IDE, como sigue:  
  
- [Modo de diseño](#vsconoperationalmodesanchor1)  
  
- [Modo de ejecución](#vsconoperationalmodesanchor2)  
  
- [Modo de interrupción](#vsconoperationalmodesanchor3)  
  
  Cómo el motor de depuración personalizado (DE) realiza la transición entre estos modos es una decisión de implementación que requiere estar familiarizado con los mecanismos de transición. La DE puede o no puede implementar directamente estos modos. Estos modos son en realidad paquete modos de depuración que cambian en función de la acción del usuario o de la DE los eventos. Por ejemplo, la transición del modo de ejecución al modo de interrupción se haya provocado por un evento de detención de la DE. La transición desde el que ejecutar modo paso a paso o modo de interrupción se haya provocado por el usuario realizando operaciones como paso o ejecutar. Para obtener más información acerca de las transiciones DE, consulte [Control de ejecución](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a> Modo de diseño  
 Modo de diseño es el estado nonrunning de depuración de Visual Studio, durante el cual puede establecer las características de la aplicación de depuración.  
  
 Solo depuración de algunas características se usan durante el modo de diseño. Un desarrollador puede establecer puntos de interrupción o crear expresiones de inspección. La DE nunca se carga o se llama mientras el IDE está en modo de diseño. Interacción con la DE tiene lugar durante los modos de ejecución e interrupción.  
  
##  <a name="vsconoperationalmodesanchor2"></a> Modo de ejecución  
 Modo de ejecución se produce cuando un programa se ejecuta en una sesión de depuración en el IDE. La aplicación se ejecuta hasta que la terminación, hasta que se alcance un punto de interrupción o hasta que se produce una excepción. Cuando se ejecuta la aplicación a la cancelación, las transiciones DE en modo de diseño. Cuando se alcanza un punto de interrupción o se produce una excepción, la DE transiciones para el modo de interrupción.  
  
##  <a name="vsconoperationalmodesanchor3"></a> Modo de interrupción  
 Modo de interrupción se produce cuando se suspende la ejecución del programa de depuración. Modo de interrupción ofrece al programador una instantánea de la aplicación en el momento de la interrupción y permite al desarrollador analizar el estado de la aplicación y cambiar cómo se ejecutará la aplicación. El desarrollador puede ver y editar código, examinar o modificar los datos, reinicie la aplicación, finalizar la ejecución o continuar la ejecución desde el mismo punto.  
  
 Modo de interrupción se especifica cuando la DE envía un evento de detención sincrónica. Eventos de detención sincrónico, también denominados eventos de detención, notifican al administrador de depuración de la sesión (SDM) y el IDE que la aplicación que se está depura ha detenido la ejecución de código. El [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) y [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) interfaces son ejemplos de eventos de detención.  
  
 Detener eventos continúan mediante una llamada a uno de los métodos siguientes, que el depurador de modo de interrupción para ejecutar o modo de paso de transición:  
  
-   [Execute](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> Modo paso a paso  
 Modo paso a paso se produce cuando el programa de los pasos a la siguiente línea de código, o en, a través o fuera de una función. Un paso se ejecuta llamando al método [paso](../../extensibility/debugger/reference/idebugprocess3-step.md). Este método requiere `DWORD`que especifican el [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) y [STEPKIND](../../extensibility/debugger/reference/stepkind.md) enumeraciones como parámetros de entrada.  
  
 Cuando el programa correctamente los pasos a la siguiente línea de código o en una función, o se ejecuta hasta el cursor o para establecer un punto de interrupción, pasa automáticamente al DE volver a modo de interrupción.  
  
## <a name="see-also"></a>Vea también  
 [Control de ejecución](../../extensibility/debugger/control-of-execution.md)