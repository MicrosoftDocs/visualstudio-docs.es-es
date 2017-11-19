---
title: Modos de funcionamiento | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 205837bc5bfdf9476839ea1e54a53dc57dbf9a72
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="operational-modes"></a>Modos de funcionamiento
Hay tres modos en los que puede operar el IDE, como se indica a continuación:  
  
-   [Modo de diseño](#vsconoperationalmodesanchor1)  
  
-   [Modo de ejecución](#vsconoperationalmodesanchor2)  
  
-   [Modo de interrupción](#vsconoperationalmodesanchor3)  
  
 Cómo el motor de depuración (Alemania) realiza la transición entre estos modos es una decisión de implementación que debe estar familiarizado con los mecanismos de transición. El Alemania puede o no puede implementar directamente estos modos. Estos modos son en realidad paquete modos de depuración que cambian en función de la acción del usuario o de la DE los eventos. Por ejemplo, la transición del modo de ejecución al modo de interrupción se haya provocado por un evento de detención de la DE. La transición de interrupción al ejecutar el modo o modo paso a paso se haya provocado por el usuario que realiza operaciones como paso o ejecutar. Para obtener más información acerca de las transiciones DE, consulte [Control de ejecución](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a>Modo de diseño  
 Modo de diseño es el estado nonrunning de depuración de Visual Studio, durante el cual puede establecer características en la aplicación de depuración.  
  
 Depuración sólo algunas características se utilizan durante el modo de diseño. Un desarrollador puede optar por establecer puntos de interrupción o crear expresiones de inspección. La DE nunca se carga o se denominan mientras que el IDE está en modo de diseño. Interacción con la DE tiene lugar durante los modos de ejecución e interrupción.  
  
##  <a name="vsconoperationalmodesanchor2"></a>Modo de ejecución  
 Modo de ejecución se produce cuando un programa se ejecuta en una sesión de depuración en el IDE. La aplicación se ejecuta hasta que la terminación, hasta que se alcanza un punto de interrupción, o hasta que se produce una excepción. Cuando se ejecuta la aplicación a la terminación, las transiciones DE en modo de diseño. Cuando se visita un punto de interrupción o se produce una excepción, la DE realiza la transición para el modo de interrupción.  
  
##  <a name="vsconoperationalmodesanchor3"></a>Modo de interrupción  
 Modo de interrupción se produce cuando se suspende la ejecución del programa de depuración. Modo de interrupción ofrece al programador una instantánea de la aplicación en el momento de la interrupción y permite al desarrollador analizar el estado de la aplicación y cambiar cómo se ejecutará la aplicación. El programador puede ver y editar código, examinar o modificar los datos, reinicie la aplicación, finalizar la ejecución o continuar la ejecución en el mismo.  
  
 Se especifica el modo de interrupción cuando la Alemania envía un evento de detención sincrónico. Notificar a los eventos de detención sincrónico, también denominados eventos de detención, el Administrador de sesión de depuración (SDM) y el IDE de la aplicación que se está depura se ha detenido la ejecución de código. El [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) y [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) interfaces son ejemplos de eventos de detención.  
  
 Detener eventos continúan mediante una llamada a uno de los métodos siguientes, que el depurador de modo de interrupción para ejecutar o modo paso a paso la transición:  
  
-   [Ejecutar](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a>Modo paso a paso  
 Modo de paso se produce cuando el programa de pasos a la siguiente línea de código, o en, en o fuera de una función. Un paso se ejecuta llamando al método [paso](../../extensibility/debugger/reference/idebugprocess3-step.md). Este método requiere `DWORD`s que especifican la [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) y [STEPKIND](../../extensibility/debugger/reference/stepkind.md) enumeraciones como parámetros de entrada.  
  
 Cuando el programa correctamente los pasos a la siguiente línea de código o a una función, o se ejecuta hasta el cursor o un punto de interrupción de conjunto, la DE pasa automáticamente atrás para el modo de interrupción.  
  
## <a name="see-also"></a>Vea también  
 [Control de ejecución](../../extensibility/debugger/control-of-execution.md)