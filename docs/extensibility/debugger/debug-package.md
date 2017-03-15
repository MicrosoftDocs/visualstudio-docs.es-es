---
title: "Depurar paquete | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], paquetes"
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Depurar paquete
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El paquete de depuración se ejecuta en el shell de Visual Studio y administra toda la interfaz de usuario.  Consume las interfaces de depuración de Visual Studio y se comunica con el administrador de depuración de la sesión \(SDM\).  
  
 Divida los eventos enviados a través del modificador de SDM el depurador de modo de ejecución en modo de interrupción y cambie el foco al programa donde la interrupción.  El paquete de depuración sigue el marco de pila y el subproceso de la información enviada al por eventos.  
  
 El paquete de depuración no tiene una dependencia del lenguaje o del entorno en tiempo de ejecución.  No es necesario implementar o modificar el paquete de depuración.  
  
 El paquete de depuración se implementa mediante vsdebug.dll.  
  
## Vea también  
 [Administrador de depuración de sesión](../../extensibility/debugger/session-debug-manager.md)   
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)   
 [Subprocesos](../../extensibility/debugger/threads.md)   
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)