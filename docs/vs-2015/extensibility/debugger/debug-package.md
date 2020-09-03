---
title: Depurar paquete | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dda8b1ac6eaa2cd5352d441600ae720c3aac321c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181292"
---
# <a name="debug-package"></a>Depurar paquete
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El paquete de depuración se ejecuta en el shell de Visual Studio y controla toda la interfaz de usuario. Consume las interfaces de depuración de Visual Studio y se comunica con el administrador de depuración de sesión (SDM).  
  
 Interrumpa los eventos enviados a través del conmutador SDM el depurador del modo de ejecución al modo de interrupción y cambie el foco al programa en el que se produjo la interrupción. El paquete de depuración realiza un seguimiento del marco de pila y del subproceso a partir de la información que se le envía a través de los eventos.  
  
 El paquete de depuración no tiene dependencias de lenguaje o de entorno en tiempo de ejecución. No es necesario implementar ni modificar el paquete de depuración.  
  
 El paquete de depuración se implementa mediante vsdebug.dll.  
  
## <a name="see-also"></a>Consulte también  
 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)   
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)   
 [ThreadPool](../../extensibility/debugger/threads.md)   
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
