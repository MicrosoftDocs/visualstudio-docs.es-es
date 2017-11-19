---
title: Depurar paquete | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eccd258476f82871732ef7b16f0282d2f945b9ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="debug-package"></a>Depurar paquete
El paquete de depuración se ejecuta en el shell de Visual Studio y encarga de toda la interfaz de usuario. Consume las interfaces de depuración de Visual Studio y se comunica con el Administrador de sesión de depuración (SDM).  
  
 Eventos de interrupción enviados a través de lo SDM cambie el depurador de modo de ejecución para el modo de interrupción y cambiar el foco al programa donde se produjo la interrupción. El paquete de depuración hace un seguimiento el marco de pila y el subproceso de la información enviada a él los eventos.  
  
 El paquete de depuración no tiene ningún idioma o las dependencias del entorno de tiempo de ejecución. No es necesario implementar o modificar el paquete de depuración.  
  
 El paquete de depuración se implementa mediante vsdebug.dll.  
  
## <a name="see-also"></a>Vea también  
 [Administrador de sesión de depuración](../../extensibility/debugger/session-debug-manager.md)   
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)   
 [Subprocesos](../../extensibility/debugger/threads.md)   
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)