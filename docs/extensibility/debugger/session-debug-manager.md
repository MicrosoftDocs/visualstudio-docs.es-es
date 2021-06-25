---
title: Administrador de depuración de sesión | Microsoft Docs
description: Obtenga información sobre el administrador de depuración de sesión, que administra varios motores de depuración que depuran programas en varios procesos en cualquier número de máquinas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 217a2d401e61c58a58d958bb754265a19a2a367d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902090"
---
# <a name="session-debug-manager"></a>Administrador de depuración de sesión
El administrador de depuración de sesión (SDM) administra cualquier número de motores de depuración (DE) que depuran cualquier número de programas en varios procesos en cualquier número de máquinas. Además de ser un multiplexor del motor de depuración, el SDM proporciona una vista unificada de la sesión de depuración para el IDE.

## <a name="session-debug-manager-operation"></a>Operación del administrador de depuración de sesión
 El administrador de depuración de sesión (SDM) administra el DE. Puede haber más de un motor de depuración en ejecución en una máquina al mismo tiempo. Para multiplexar los DE, el SDM encapsula varias interfaces de los DE y las expone al IDE como una sola interfaz.

 Para aumentar el rendimiento, algunas interfaces no se multiplexa. En su lugar, se usan directamente desde el DE y las llamadas a estas interfaces no pasan por el SDM. Por ejemplo, las interfaces usadas con contextos de memoria, código y documento no se multiplexan, porque hacen referencia a una instrucción, memoria o documento específicos de un programa específico depurado por un DE específico. Ningún otro DE debe estar implicado en ese nivel de comunicación.

 Esto no es cierto en todos los contextos. Las llamadas a la interfaz de contexto de evaluación de expresiones pasan por el SDM. Durante la evaluación de expresiones, SDM encapsula la interfaz [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) que proporciona al IDE porque, cuando se evalúa esa expresión, puede implicar varios DE que están depurando programas en el mismo proceso que podrían ejecutarse en el mismo subproceso.

 El SDM suele actuar como mecanismo de delegación, pero puede actuar como mecanismo de difusión. Por ejemplo, durante la evaluación de expresiones, el SDM actúa como un mecanismo de difusión para notificar a todos los DE que pueden ejecutar código en un subproceso especificado. De forma similar, cuando el SDM recibe un evento de detención, difunde a los programas que deben dejar de ejecutarse. Cuando se llama a un paso, el SDM difunde a los programas que pueden seguir ejecutando. Los puntos de interrupción también se difunden a cada DE.

 El SDM no realiza el seguimiento del programa, subproceso o marco de pila actuales. La información de proceso, programa y subproceso se envía al SDM junto con eventos de depuración específicos.

## <a name="see-also"></a>Consulta también
- [Motor de depuración](../../extensibility/debugger/debug-engine.md)
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
- [Contextos del depurador](../../extensibility/debugger/debugger-contexts.md)
