---
title: Depurar paquete | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb1af813fabb1245d85fe18629d77a45f6acca3f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345903"
---
# <a name="debug-package"></a>Depurar el paquete
El paquete de depuración se ejecuta en el shell de Visual Studio y encarga de toda la interfaz de usuario. Se consume el interfaces de depuración de Visual Studio y se comunica con el Administrador de depuración de la sesión (SDM).

 Eventos de interrupción que se envían a través el SDM cambie el depurador de modo de ejecución para el modo de interrupción y cambiar el foco al programa donde se produjo la interrupción. El paquete de depuración hace un seguimiento el marco de pila y el subproceso de la información que recibe de los eventos.

 El paquete de depuración no tiene ningún idioma o las dependencias del entorno de tiempo de ejecución. No es necesario implementar o modificar el paquete de depuración.

 El paquete de depuración se implementa mediante *vsdebug.dll*.

## <a name="see-also"></a>Vea también
- [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)
- [Marcos de pila](../../extensibility/debugger/stack-frames.md)
- [Subprocesos](../../extensibility/debugger/threads.md)
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)