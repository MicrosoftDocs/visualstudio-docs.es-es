---
title: Depurar paquete | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 61df51b422660a5ea116f136b0d5183e59293a02
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286330"
---
# <a name="debug-package"></a>Depurar paquete
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El paquete de depuración se ejecuta en el shell de Visual Studio y encarga de toda la interfaz de usuario. Se consume el interfaces de depuración de Visual Studio y se comunica con el Administrador de depuración de la sesión (SDM).  
  
 Eventos de interrupción que se envían a través el SDM cambie el depurador de modo de ejecución para el modo de interrupción y cambiar el foco al programa donde se produjo la interrupción. El paquete de depuración hace un seguimiento el marco de pila y el subproceso de la información que recibe de los eventos.  
  
 El paquete de depuración no tiene ningún idioma o las dependencias del entorno de tiempo de ejecución. No es necesario implementar o modificar el paquete de depuración.  
  
 Vsdebug.dll implementa el paquete de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)   
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)   
 [Subprocesos](../../extensibility/debugger/threads.md)   
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)

