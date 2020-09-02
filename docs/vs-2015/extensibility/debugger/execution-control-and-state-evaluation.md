---
title: Control de ejecución y evaluación de estado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc6476c925f37d70ab45bae129a8b8a379ee519c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152769"
---
# <a name="execution-control-and-state-evaluation"></a>Control de ejecución y evaluación de estado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La depuración de una aplicación requiere la implementación de dichas características de control de ejecución como ejecutar paso a paso las funciones, detener en puntos de interrupción y continuar la ejecución. La depuración de Visual Studio basa su control de ejecución en eventos enviados entre los componentes del depurador.  
  
## <a name="in-this-section"></a>En esta sección  
 [Control de programas](../../extensibility/debugger/program-control.md)  
 Enumera las siguientes rutinas que se producen en el nivel de programa: establecimiento de la siguiente instrucción, ejecución, ejecución paso a paso, continuación, suspensión y reanudación.  
  
 [Métodos relacionados con el punto de interrupción](../../extensibility/debugger/breakpoint-related-methods.md)  
 Define los tipos de puntos de interrupción enlazados y pendientes que admite Visual Studio.  
  
 [Evaluación de la pila de llamadas](../../extensibility/debugger/call-stack-evaluation.md)  
 Describe la implementación de los métodos que permiten la visualización de los marcos de pila de la pila de llamadas durante el modo de interrupción.  
  
 [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Explica cómo el motor de depuración (DE), la evaluación de expresiones (EE) y el administrador de depuración de sesión están implicados en el análisis y la evaluación de una expresión especificada en una de las ventanas del IDE.  
  
 [Eventos de control](../../extensibility/debugger/control-events.md)  
 Describe la interfaz utilizada para enviar eventos durante la ejecución controlada del programa.
