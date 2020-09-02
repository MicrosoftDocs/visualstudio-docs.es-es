---
title: Administrador de depuración de sesión | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157829"
---
# <a name="session-debug-manager"></a>Administrador de depuración de sesión
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El administrador de depuración de sesión (SDM) administra cualquier número de motores de depuración (depuración) de cualquier número de programas en varios procesos en cualquier número de equipos. Además de ser un multiplexor del motor de depuración, el SDM proporciona una vista unificada de la sesión de depuración al IDE.  
  
## <a name="session-debug-manager-operation"></a>Operación del administrador de depuración de sesión  
 El administrador DE depuración de sesión (SDM) administra la DE. Puede haber más de un motor de depuración en ejecución en un equipo al mismo tiempo. Para multiplexar el DEs, el SDM incluye un número de interfaces del DEs y las expone al IDE como una sola interfaz.  
  
 Para aumentar el rendimiento, algunas interfaces no se multiplexan. En su lugar, se usan directamente desde el DE y las llamadas a estas interfaces no pasan por el SDM. Por ejemplo, las interfaces utilizadas con los contextos de memoria, código y documento no se multiplexan, porque hacen referencia a una instrucción específica, memoria o documento en un programa específico depurado por un determinado DE. No es necesario que ningún otro de esté implicado en ese nivel de comunicación.  
  
 Esto no es cierto para todos los contextos. Las llamadas a la interfaz de contexto de evaluación de expresiones pasan por el SDM. Durante la evaluación de la expresión, el SDM encapsula la interfaz [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) que proporciona al IDE porque, cuando se evalúa esa expresión, puede implicar varios des que depuran programas en el mismo proceso que podrían estar ejecutándose en el mismo subproceso.  
  
 El SDM actúa normalmente como un mecanismo de delegación, pero podría actuar como mecanismo de difusión. Por ejemplo, durante la evaluación de expresiones, el SDM actúa como un mecanismo de difusión para notificar a todo DEs que puede ejecutar código en un subproceso especificado. Del mismo modo, cuando el SDM recibe un evento de detención, se difunde a todos los programas que deben dejar de ejecutarse. Cuando se llama a un paso, el SDM se difunde a todos los programas que pueden seguir en ejecución. Los puntos DE interrupción también se difunden a cada DE.  
  
 El SDM no realiza el seguimiento del programa, el subproceso o el marco de pila actual. La información sobre el proceso, el programa y el subproceso se envía al SDM junto con eventos específicos de depuración.  
  
## <a name="see-also"></a>Consulte también  
 [Motor de depuración](../../extensibility/debugger/debug-engine.md)   
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)   
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)
