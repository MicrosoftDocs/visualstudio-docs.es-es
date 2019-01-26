---
title: Control de ejecución y evaluación de estado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e71fb57a4890c29652473338391a0f7181d19ac0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010420"
---
# <a name="execution-control-and-state-evaluation"></a>Evaluación de control y el estado de ejecución
Depurar una aplicación requiere la implementación de funcionalidades de control de ejecución como ejecutar funciones, la detención en puntos de interrupción y continuar la ejecución. Bases de depuración de Visual Studio su control de ejecución en los eventos se envía entre los componentes del depurador.  
  
## <a name="in-this-section"></a>En esta sección  
 [Control del programa](../../extensibility/debugger/program-control.md)  
 Enumera las rutinas siguientes que se producen en el nivel de programa: establecer la instrucción siguiente, ejecutar, ejecución paso a paso, continuar, suspender y reanudar.  
  
 [Métodos relacionados con el punto de interrupción](../../extensibility/debugger/breakpoint-related-methods.md)  
 Define el límite y pendiente de tipos de puntos de interrupción que es compatible con Visual Studio.  
  
 [Evaluación de la pila de llamadas](../../extensibility/debugger/call-stack-evaluation.md)  
 Describe la implementación de los métodos que permiten ver los marcos de pila de la pila de llamadas durante el modo de interrupción.  
  
 [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Explica cómo el motor de depuración (DE), Administrador de expresiones evaluación (EE) y la sesión de depuración están implicadas en el análisis y evaluación de una expresión especificada en una de las ventanas del IDE.  
  
 [Eventos de control](../../extensibility/debugger/control-events.md)  
 Describe la interfaz que se usa para enviar eventos durante la ejecución del programa controlada.