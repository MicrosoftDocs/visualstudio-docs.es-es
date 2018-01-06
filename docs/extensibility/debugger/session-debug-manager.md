---
title: "Administrador de sesión de depuración | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7d7acd147fd8d2b73b2172900baf7e1f49808e9a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="session-debug-manager"></a>Administrador de sesión de depuración
El Administrador de sesión de depuración (SDM) administra cualquier número de motores de depuración (Alemania) cualquier número de programas en varios procesos en un número indeterminado de máquinas de depuración. Además de ser un motor de depuración multiplexor, el SDM proporciona una vista unificada de la sesión de depuración para el IDE.  
  
## <a name="session-debug-manager-operation"></a>Operación del Administrador de depuración de sesión  
 El Administrador de sesión de depuración (SDM) administra la Alemania. Puede haber más de un motor de depuración que se ejecuta en un equipo al mismo tiempo. Para multiplexar el DEs, el SDM ajusta una serie de interfaces del DEs y los expone el IDE como una única interfaz.  
  
 Para aumentar el rendimiento, no se multiplexan algunas interfaces. En su lugar, se utilizan directamente desde el Alemania y llamadas a estas interfaces no pasar por el SDM. Por ejemplo, interfaces usadas con memoria, código y los contextos de documento no se multiplexan, porque hacen referencia a una instrucción específica, memoria o documento en un determinado programa depurado por un específico DE. No hay otro Alemania debe participar en el nivel de comunicación.  
  
 Esto no es cierto de todos los contextos. Llamadas a la interfaz de contexto de evaluación de expresión pasan a través de lo SDM. Al evaluar una expresión, se ajusta el SDM el [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaz que proporciona el IDE porque cuando se evalúa la expresión, puede implicar varios DEs que va a depurar programas en el mismo proceso que podrían ser se ejecuta en el mismo subproceso.  
  
 El SDM normalmente actúa como un mecanismo de delegación, pero sí puede actuar como un mecanismo de difusión. Por ejemplo, al evaluar una expresión, el SDM actúa como un mecanismo de difusión para notificar DEs todos los que puede ejecutar el código en un subproceso especificado. De forma similar, cuando el SDM recibe un evento de detención, difunde a todos los programas que deben dejar de ejecutarse. Cuando se llama a un paso, difunde el SDM en todos los programas que puede continuar ejecutándose. Los puntos de interrupción también se difunden a cada Alemania.  
  
 El SDM no realiza un seguimiento del programa actual, el subproceso o el marco de pila. El proceso, el programa y el subproceso se envía información a la SDM junto con eventos específicos de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)