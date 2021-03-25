---
title: Depurar paquete | Microsoft Docs
description: Obtenga información sobre cómo se ejecuta el paquete de depuración en Visual Studio Shell y controla la interfaz de usuario mediante la utilización de las interfaces de depuración y la comunicación con el administrador de depuración de sesión.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90c4c82895f7a30d4df9126a280c6c9ffa7ffa76
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067912"
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
