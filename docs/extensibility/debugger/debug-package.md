---
title: Depurar paquete | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04eb6802cabd4ae36151580c573d28b977ca348e
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204049"
---
# <a name="debug-package"></a>Depurar el paquete
El paquete de depuración se ejecuta en el shell de Visual Studio y encarga de toda la interfaz de usuario. Se consume el interfaces de depuración de Visual Studio y se comunica con el Administrador de depuración de la sesión (SDM).  
  
 Eventos de interrupción que se envían a través el SDM cambie el depurador de modo de ejecución para el modo de interrupción y cambiar el foco al programa donde se produjo la interrupción. El paquete de depuración hace un seguimiento el marco de pila y el subproceso de la información que recibe de los eventos.  
  
 El paquete de depuración no tiene ningún idioma o las dependencias del entorno de tiempo de ejecución. No es necesario implementar o modificar el paquete de depuración.  
  
 El paquete de depuración se implementa mediante *vsdebug.dll*.  
  
## <a name="see-also"></a>Vea también  
 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)   
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)   
 [Subprocesos](../../extensibility/debugger/threads.md)   
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)