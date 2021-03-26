---
title: Administrador de depuración de sesión | Microsoft Docs
description: Obtenga información sobre el administrador de depuración de la sesión, que administra varios programas de depuración de motores de depuración en varios procesos en cualquier número de equipos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2e5a206b8ece21b14758dfeb02563d4d323dcf60
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079467"
---
# <a name="session-debug-manager"></a>Administrador de depuración de sesión
El administrador de depuración de sesión (SDM) administra cualquier número de motores de depuración (DE) que depuren cualquier número de programas en varios procesos en cualquier número de equipos. Además de ser un multiplexor del motor de depuración, el SDM proporciona una vista unificada de la sesión de depuración al IDE.

## <a name="session-debug-manager-operation"></a>Operación del administrador de depuración de sesión
 El administrador DE depuración de sesión (SDM) administra la DE. Puede haber más de un motor de depuración en ejecución en un equipo al mismo tiempo. Para multiplexar el DEs, el SDM incluye un número de interfaces del DEs y las expone al IDE como una sola interfaz.

 Para aumentar el rendimiento, algunas interfaces no se multiplexan. En su lugar, se usan directamente desde el DE y las llamadas a estas interfaces no pasan por el SDM. Por ejemplo, las interfaces utilizadas con los contextos de memoria, código y documento no se multiplexan, porque hacen referencia a una instrucción específica, memoria o documento en un programa específico depurado por un determinado DE. No es necesario que ningún otro de esté implicado en ese nivel de comunicación.

 Esto no es cierto para todos los contextos. Las llamadas a la interfaz de contexto de evaluación de expresiones pasan por el SDM. Durante la evaluación de la expresión, el SDM encapsula la interfaz [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) que proporciona al IDE porque, cuando se evalúa esa expresión, puede implicar varios des que depuran programas en el mismo proceso que podrían estar ejecutándose en el mismo subproceso.

 El SDM actúa normalmente como un mecanismo de delegación, pero podría actuar como mecanismo de difusión. Por ejemplo, durante la evaluación de expresiones, el SDM actúa como un mecanismo de difusión para notificar a todo DEs que puede ejecutar código en un subproceso especificado. Del mismo modo, cuando el SDM recibe un evento de detención, difunde a los programas que deben dejar de ejecutarse. Cuando se llama a un paso, el SDM se difunde a los programas que pueden seguir en ejecución. Los puntos DE interrupción también se difunden a cada DE.

 El SDM no realiza el seguimiento del programa, el subproceso o el marco de pila actual. El proceso, el programa y la información de subprocesos se envían al SDM junto con eventos de depuración específicos.

## <a name="see-also"></a>Consulte también
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
