---
title: Depurar paquete | Microsoft Docs
description: Obtenga información sobre cómo se ejecuta el paquete de depuración en Visual Studio Shell y controla la interfaz de usuario mediante la utilización de las interfaces de depuración y la comunicación con el administrador de depuración de sesión.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad62a487d38500617999a276aa3ae15a75089736
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914132"
---
# <a name="debug-package"></a>Depurar paquete
El paquete de depuración se ejecuta en el shell de Visual Studio y controla toda la interfaz de usuario. Consume las interfaces de depuración de Visual Studio y se comunica con el administrador de depuración de sesión (SDM).

 Interrumpa los eventos enviados a través del conmutador SDM el depurador del modo de ejecución al modo de interrupción y cambie el foco al programa en el que se produjo la interrupción. El paquete de depuración realiza un seguimiento del marco de pila y del subproceso a partir de la información que se le envía a través de los eventos.

 El paquete de depuración no tiene dependencias de lenguaje o de entorno en tiempo de ejecución. No es necesario implementar ni modificar el paquete de depuración.

 El paquete de depuración se implementa mediante *vsdebug.dll*.

## <a name="see-also"></a>Consulte también
- [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)
- [Marcos de pila](../../extensibility/debugger/stack-frames.md)
- [Subprocesos](../../extensibility/debugger/threads.md)
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
