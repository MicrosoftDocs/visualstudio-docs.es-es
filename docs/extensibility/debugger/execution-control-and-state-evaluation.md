---
title: Control de la ejecución y el estado de evaluación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d306ffe484605a081afa81afdcdcaa1a70339c84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098178"
---
# <a name="execution-control-and-state-evaluation"></a>Control de la ejecución y evaluación de estado
Depurar una aplicación requiere la implementación de estas características de control de ejecución como la ejecución paso a paso en funciones, deténgase en los puntos de interrupción y continuar la ejecución. La depuración de bases de datos de Visual Studio su control de ejecución en los eventos enviados entre los componentes del depurador.  
  
## <a name="in-this-section"></a>En esta sección  
 [Control de programas](../../extensibility/debugger/program-control.md)  
 Enumera las rutinas siguientes que se producen en el nivel de programa: establecer la siguiente instrucción, ejecutar, ejecución paso a paso, continuar, suspender y reanudar.  
  
 [Métodos relacionados con el punto de interrupción](../../extensibility/debugger/breakpoint-related-methods.md)  
 Define el límite y pendiente de tipos de puntos de interrupción que es compatible con Visual Studio.  
  
 [Evaluación de la pila de llamadas](../../extensibility/debugger/call-stack-evaluation.md)  
 Describe la implementación de los métodos que permiten ver los marcos de pila de la pila de llamadas durante el modo de interrupción.  
  
 [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Explica cómo el motor de depuración (Alemania), Administrador de expresiones evaluación (EE) y la sesión de depuración están implicados en el análisis y evaluación de una expresión especificada en una de las ventanas del IDE.  
  
 [Eventos de control](../../extensibility/debugger/control-events.md)  
 Describe la interfaz usada para enviar eventos durante la ejecución del programa controlada.