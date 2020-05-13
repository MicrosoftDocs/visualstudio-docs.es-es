---
title: Control de Ejecución y Evaluación del Estado (State Control) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738756"
---
# <a name="execution-control-and-state-evaluation"></a>Control de ejecución y evaluación del estado
Depurar una aplicación requiere implementar características de control de ejecución como entrar en funciones, detener en puntos de interrupción y continuar la ejecución. La depuración de Visual Studio basa su control de ejecución en eventos enviados entre componentes del depurador.

## <a name="in-this-section"></a>En esta sección
 [Control del programa](../../extensibility/debugger/program-control.md) Enumera las siguientes rutinas que se producen en el nivel de programa: establecer la siguiente instrucción, ejecutar, paso a paso, continuar, suspender y reanudar.

 [Métodos relacionados con](../../extensibility/debugger/breakpoint-related-methods.md) el punto de interrupción Define los tipos enlazados y pendientes de puntos de interrupción que admite Visual Studio.

 [Evaluación de pila de llamadas](../../extensibility/debugger/call-stack-evaluation.md) Describe la implementación de los métodos que permiten la visualización de los marcos de pila de la pila de llamadas durante el modo de interrupción.

 [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Explica cómo el motor de depuración (DE), la evaluación de expresiones (EE) y el administrador de depuración de sesión participan en el análisis y la evaluación de una expresión introducida en una de las ventanas del IDE.

 [Eventos de control](../../extensibility/debugger/control-events.md) Describe la interfaz utilizada para enviar eventos durante la ejecución controlada del programa.
