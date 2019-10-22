---
title: Sesión de administrador de depuración | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fd7c7555c19f850a15161f6fba00b1184621a9e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157829"
---
# <a name="session-debug-manager"></a>Administrador de depuración de sesión
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El Administrador de depuración de la sesión (SDM) administra cualquier número de motores de depuración (DE) cualquier número de programas en varios procesos en cualquier número de equipos de depuración. Además de ser un multiplexor de motor de depuración, el SDM proporciona una vista unificada de la sesión de depuración para el IDE.  
  
## <a name="session-debug-manager-operation"></a>Operación de sesión de administrador de depuración  
 El Administrador de depuración de la sesión (SDM) administra la DE. Puede haber más de un motor de depuración que se ejecutan en un equipo al mismo tiempo. Para multiplexar los DEs, el SDM incluye un número de interfaces de la DEs y los expone el IDE como una única interfaz.  
  
 Para aumentar el rendimiento, no se multiplexan algunas interfaces. En su lugar, se utilizan directamente desde la DE, y las llamadas a estas interfaces no pasan por el SDM. Por ejemplo, las interfaces utilizadas con la memoria, el código y contextos de documento no se multiplexan, porque hacen referencia a una instrucción específica, memoria o documento en un determinado programa depurado por una específica DE. No DE otro debe participar en el nivel de comunicación.  
  
 Esto no es cierto de todos los contextos. Las llamadas a la interfaz de contexto de evaluación de expresión pasar por el SDM. Durante la evaluación de expresión, se ajusta el SDM el [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz que proporciona el IDE porque cuando se evalúa la expresión, puede implicar varios DEs que va a depurar programas en el mismo proceso que podría ser que se ejecutan en el mismo subproceso.  
  
 El SDM normalmente actúa como un mecanismo de delegación, pero sí puede actuar como un mecanismo de difusión. Por ejemplo, durante la evaluación de expresión, el SDM actúa como un mecanismo de difusión para notificar a todos los DEs que puede ejecutar el código en un subproceso especificado. De forma similar, cuando el SDM recibe un evento de detención, difunde todos los programas que debe dejar de ejecutarse. Cuando se llama a un paso, el SDM difunde a todos los programas que puede seguir ejecutándose. Los puntos de interrupción también se difunden a cada DE.  
  
 El SDM no realiza un seguimiento del programa actual, el subproceso o marco de pila. El proceso, el programa y el subproceso se envía información al SDM junto con eventos específicos de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)
