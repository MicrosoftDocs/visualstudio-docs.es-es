---
title: "Enviar los eventos necesarios | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], eventos necesaria"
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Enviar los eventos necesarios
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice este procedimiento para enviar eventos necesarios.  
  
## Proceso para los eventos de Sending Requerido  
 Los eventos siguientes son necesarios, en este orden, al crear un motor de depuración \(DE\) y adjuntándola a un programa:  
  
1.  Enviar un objeto de evento de [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) el administrador de depuración de la sesión \(SDM\) cuando el OF se inicializa para depurar uno o más programas en un proceso.  
  
2.  Cuando el programa que se va a depurar se adjunta a, envíe un objeto de evento de [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al SDM.  Este evento puede ser un evento que detiene, dependiendo del diseño del motor.  
  
3.  Si el programa se adjunta a cuando se inicia el proceso, envíe un objeto de evento de [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) al SDM para notificar al IDE del nuevo subproceso.  Este evento puede ser un evento que detiene, dependiendo del diseño del motor.  
  
4.  Enviar un objeto de evento de [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) al SDM cuando el programa que se está depurando se termina de cargar o al adjuntar el programa se completa.  este evento debe ser un evento que detiene.  
  
5.  Si se inicia la aplicación para depurar, envíe un objeto de evento de [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) al SDM cuando la primera instrucción de código en la arquitectura en tiempo de ejecución está a punto de ejecutarse.  este evento es siempre un evento que detiene.  Al examinar la sesión de depuración, el IDE se detiene en este evento.  
  
> [!NOTE]
>  Muchos lenguajes utilizan inicializadores o el externo globales, funciones precompiladas \(de la biblioteca o de \_Main CRT\) al principio del código.  Si el idioma del programa que se está depurando contiene cualquiera de estos tipos de elementos antes del punto de entrada inicial, se ejecuta este código y se envía el evento de punto de entrada cuando el punto de entrada de usuario, como **Principal** o `WinMain`, se alcance.  
  
## Vea también  
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)