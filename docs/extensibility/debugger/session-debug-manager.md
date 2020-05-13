---
title: Administrador de depuración de sesión ( Session Debug Manager) Microsoft Docs
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 953b4e948ef5e21531a3e73bceed3a363ed3cec5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712883"
---
# <a name="session-debug-manager"></a>Administrador de depuración de sesión
El administrador de depuración de sesión (SDM) administra cualquier número de motores de depuración (DE) que están depurando cualquier número de programas en varios procesos en cualquier número de máquinas. Además de ser un multiplexor del motor de depuración, el SDM proporciona una vista unificada de la sesión de depuración al IDE.

## <a name="session-debug-manager-operation"></a>Operación del administrador de depuración de sesión
 El administrador de depuración de sesión (SDM) administra el DE. Puede haber más de un motor de depuración ejecutándose en una máquina al mismo tiempo. Para multiplexar los DE, el SDM ajusta una serie de interfaces de los DE y los expone al IDE como una sola interfaz.

 Para aumentar el rendimiento, algunas interfaces no se multiplexan. En lugar, se utilizan directamente del DE, y las llamadas a estas interfaces no pasan a través del SDM. Por ejemplo, las interfaces utilizadas con contextos de memoria, código y documento no se multiplexan, porque hacen referencia a una instrucción, memoria o documento específico según un programa específico depurado por un DE específico. Ningún otro DE necesita estar involucrado en ese nivel de comunicación.

 Esto no es cierto en todos los contextos. Las llamadas a la interfaz de contexto de evaluación de expresiones pasan por el SDM. Durante la evaluación de expresiones, el SDM ajusta el [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz que proporciona al IDE porque cuando se evalúa esa expresión, puede implicar varios DE que están depurando programas en el mismo proceso que podrían ejecutarse en el mismo subproceso.

 El SDM actúa típicamente como un mecanismo de delegación, pero podría actuar como un mecanismo de difusión. Por ejemplo, durante la evaluación de expresiones, el SDM actúa como un mecanismo de difusión para notificar a todos los DE que pueden ejecutar código en un subproceso especificado. De forma similar, cuando el SDM recibe un evento de detención, transmite a los programas que deben dejar de ejecutarse. Cuando se llama a un paso, el SDM difunde a los programas que pueden continuar ejecutándose. Los puntos de interrupción también se transmiten a cada DE.

 El SDM no realiza un seguimiento del programa, el subproceso o el marco de pila actuales. La información de proceso, programa y subproceso se envía al SDM junto con eventos de depuración específicos.

## <a name="see-also"></a>Vea también
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
