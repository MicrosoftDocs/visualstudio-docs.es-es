---
title: Envío de los eventos necesarios | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 457e2daf3e52c23ba9733d09d3aeb94750b5fab9
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2020
ms.locfileid: "90843222"
---
# <a name="sending-the-required-events"></a>Envío de los eventos necesarios
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilice este procedimiento para enviar eventos necesarios.  
  
## <a name="process-for-sending-required-events"></a>Proceso para enviar eventos necesarios  
 Los eventos siguientes son necesarios, en este orden, al crear un motor DE depuración (DE) y asociarlo a un programa:  
  
1. Envíe un objeto de evento [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al administrador de depuración de la sesión (SDM) cuando el de se inicializa para depurar uno o varios programas en un proceso.  
  
2. Cuando el programa que se va a depurar está asociado a, envíe un objeto de evento [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al SDM. Este evento puede ser un evento de detención, dependiendo del diseño del motor.  
  
3. Si el programa está asociado a cuando se inicia el proceso, envíe un objeto de evento [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) al SDM para notificar al IDE del nuevo subproceso. Este evento puede ser un evento de detención, dependiendo del diseño del motor.  
  
4. Envíe un objeto de evento [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) al SDM cuando el programa que se está depurando termine de cargarse o cuando se complete la asociación con el programa. Este evento debe ser un evento de detención.  
  
5. Si se inicia la aplicación que se va a depurar, envíe un objeto de evento [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) al SDM cuando la primera instrucción del código de la arquitectura en tiempo de ejecución esté a punto de ejecutarse. Este evento siempre es un evento de detención. Al entrar en la sesión de depuración, el IDE se detiene en este evento.  
  
> [!NOTE]
> Muchos lenguajes utilizan inicializadores globales o funciones externas precompiladas (de la biblioteca CRT o _Main) al principio de su código. Si el idioma del programa que se está depurando contiene cualquiera de estos tipos de elementos antes del punto de entrada inicial, se ejecuta este código y se envía el evento de punto de entrada cuando se alcanza el punto de entrada del usuario, como **Main** o `WinMain` ,.  
  
## <a name="see-also"></a>Consulte también  
 [Habilitación de un programa que se va a depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
