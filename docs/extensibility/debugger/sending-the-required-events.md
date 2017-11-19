---
title: Enviar los eventos necesarios | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30a5b1150d44c138465db36da2b032b71f075397
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="sending-the-required-events"></a>Enviar los eventos necesarios
Utilice este procedimiento para enviar los eventos necesarios.  
  
## <a name="process-for-sending-required-events"></a>Proceso para enviar los eventos necesarios  
 Los eventos siguientes son necesarios, en este orden, al crear una depuración motor (Alemania) y adjuntarlo a un programa:  
  
1.  Enviar una [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) objeto de evento para el Administrador de sesión de depuración (SDM) cuando se inicializa el Alemania para uno o más programas en un proceso de depuración.  
  
2.  Cuando el programa que desea depurar se adjunta a, enviar un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) objeto de evento para el SDM. Este evento puede ser un evento de detención, según su diseño de motor.  
  
3.  Si el programa que está asociado a cuando se inicia el proceso, envíe un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) objeto de evento para el SDM para notificar el IDE del nuevo subproceso. Este evento puede ser un evento de detención, según su diseño de motor.  
  
4.  Enviar una [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) objeto de evento para el SDM cuando el programa que se está depurando se terminó de cargarse o cuando se completa la asociar al programa. Este evento debe ser un evento de detención.  
  
5.  Si se inicia la aplicación va a depurar, envíe un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) objeto de evento para el SDM cuando la primera instrucción del código de la arquitectura del tiempo de ejecución está a punto de ejecutarse. Este evento siempre es un evento de detención. Cuando ejecuta paso a paso la sesión de depuración, el IDE se detiene en este evento.  
  
> [!NOTE]
>  Muchos lenguajes usan inicializadores globales o funciones externas precompiladas (desde la biblioteca CRT o _Main) al principio de su código. Si el idioma del programa que se está depurando contiene uno de estos tipos de elementos antes del punto de entrada inicial, a continuación, se ejecuta este código y se envía el evento de punto de entrada cuando el usuario del punto de entrada, como **principal** o `WinMain`, se ha alcanzado.  
  
## <a name="see-also"></a>Vea también  
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)