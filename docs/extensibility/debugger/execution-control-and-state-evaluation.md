---
title: "Control de la ejecución y el estado de evaluación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f2f76f97111f24a7b6b4ea1a7a22004d6867fcd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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