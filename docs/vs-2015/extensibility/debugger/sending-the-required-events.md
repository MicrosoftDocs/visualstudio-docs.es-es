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
ms.openlocfilehash: 4d2e6f5213f5b12c38ed5529551c47654231035c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091081"
---
# <a name="sending-the-required-events"></a>Envío de los eventos necesarios
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Utilice este procedimiento para enviar los eventos necesarios.  
  
## <a name="process-for-sending-required-events"></a>Proceso para el envío de eventos necesarios  
 Los eventos siguientes son necesarios, en este orden, cuando el motor de creación de una depuración (DE) y conectarlo a un programa:  
  
1. Enviar una [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) objeto event para el Administrador de depuración de la sesión (SDM) cuando se inicializa la DE uno o más programas en un proceso de depuración.  
  
2. Cuando el programa que se desea depurar se adjunta a, enviar un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) objeto event para el SDM. Este evento puede ser un evento de detención, dependiendo del diseño del motor.  
  
3. Si el programa está asociado a cuando se inicia el proceso, envíe un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) objeto event para el SDM para notificar el IDE del nuevo subproceso. Este evento puede ser un evento de detención, dependiendo del diseño del motor.  
  
4. Enviar una [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) objeto event para el SDM cuando el programa que se está depurando se termina de cargar o cuando se completa la asociación al programa. Este evento debe ser un evento de detención.  
  
5. Si se inicia la aplicación que se desea depurar, envíe un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) objeto event para el SDM cuando la primera instrucción de código en la arquitectura en tiempo de ejecución que se va a ejecutar. Este evento siempre es un evento de detención. Cuando a la sesión de depuración, el IDE se detiene en este evento.  
  
> [!NOTE]
>  Muchos lenguajes usan inicializadores globales o funciones externas precompiladas (desde la biblioteca de CRT o _Main) al principio de su código. Si el idioma del programa que está depurando contiene cualquiera de estos tipos de elementos antes del punto de entrada inicial, a continuación, se ejecuta este código y se envía el evento de punto de entrada cuando el usuario punto de entrada, tales como **principal** o `WinMain`, se ha alcanzado.  
  
## <a name="see-also"></a>Vea también  
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
