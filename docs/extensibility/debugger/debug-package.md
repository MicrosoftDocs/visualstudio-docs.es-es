---
title: Depuración de paquetes | Microsoft Docs
description: Obtenga información sobre cómo se ejecuta el paquete de depuración en Visual Studio Shell y controla la interfaz de usuario mediante el consumo de las interfaces de depuración y la comunicación con el administrador de depuración de sesión.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8be920ae352067a6e77593ca0a922474d68851d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905675"
---
# <a name="debug-package"></a>Paquete de depuración
El paquete de depuración se ejecuta en Visual Studio shell y controla toda la interfaz de usuario. Consume las interfaces Visual Studio depuración y se comunica con el administrador de depuración de sesión (SDM).

 Los eventos de interrupción enviados a través de SDM cambian el depurador del modo de ejecución al modo de interrupción y cambian el foco al programa donde se produjo la interrupción. El paquete de depuración realiza un seguimiento del marco de pila y el subproceso de la información que le envían los eventos.

 El paquete de depuración no tiene dependencias de entorno en tiempo de ejecución o lenguaje. No es necesario implementar ni modificar el paquete de depuración.

 El paquete de depuración se implementa *mediantevsdebug.dll*.

## <a name="see-also"></a>Consulta también
- [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)
- [Marcos de pila](../../extensibility/debugger/stack-frames.md)
- [Subprocesos](../../extensibility/debugger/threads.md)
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
