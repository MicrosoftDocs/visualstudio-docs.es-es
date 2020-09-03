---
title: Control de ejecución y evaluación de estado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc76ae97e8baa6ce78dd4d565109d6a19e2051e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738756"
---
# <a name="execution-control-and-state-evaluation"></a>Control de ejecución y evaluación del estado
La depuración de una aplicación requiere la implementación de dichas características de control de ejecución como ejecutar paso a paso las funciones, detener en puntos de interrupción y continuar la ejecución. La depuración de Visual Studio basa su control de ejecución en eventos enviados entre los componentes del depurador.

## <a name="in-this-section"></a>En esta sección
 [Control de programas](../../extensibility/debugger/program-control.md) Enumera las siguientes rutinas que se producen en el nivel de programa: establecimiento de la siguiente instrucción, ejecución, ejecución paso a paso, continuación, suspensión y reanudación.

 [Métodos relacionados con los puntos de interrupción](../../extensibility/debugger/breakpoint-related-methods.md) Define los tipos de puntos de interrupción enlazados y pendientes que admite Visual Studio.

 [Evaluación](../../extensibility/debugger/call-stack-evaluation.md) de la pila de llamadas Describe la implementación de los métodos que permiten la visualización de los marcos de pila de la pila de llamadas durante el modo de interrupción.

 [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Explica cómo el motor de depuración (DE), la evaluación de expresiones (EE) y el administrador de depuración de sesión están implicados en el análisis y la evaluación de una expresión especificada en una de las ventanas del IDE.

 [Eventos de control](../../extensibility/debugger/control-events.md) Describe la interfaz utilizada para enviar eventos durante la ejecución controlada del programa.
