---
title: Paquete de depuración ( Debug Package) Microsoft Docs
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
ms.openlocfilehash: de6240ea5d938d02f8415009203962e124ff049e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739025"
---
# <a name="debug-package"></a>Paquete de depuración
El paquete de depuración se ejecuta en el shell de Visual Studio y controla toda la interfaz de usuario. Consume las interfaces de depuración de Visual Studio y se comunica con el administrador de depuración de sesión (SDM).

 Los eventos de interrupción enviados a través del SDM cambian el depurador del modo de ejecución al modo de interrupción y cambian el foco al programa donde se produjo la interrupción. El paquete de depuración realiza un seguimiento del marco de pila y el subproceso de la información que le envían los eventos.

 El paquete de depuración no tiene dependencias de entorno de idioma o en tiempo de ejecución. No es necesario implementar o modificar el paquete de depuración.

 El paquete de depuración se implementa mediante *vsdebug.dll*.

## <a name="see-also"></a>Vea también
- [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)
- [Marcos de pila](../../extensibility/debugger/stack-frames.md)
- [Hilos](../../extensibility/debugger/threads.md)
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
