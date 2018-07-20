---
title: Asociación directamente a un programa | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1fa232e0e8bfca31d16209ca8cb7acd15954940
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151790"
---
# <a name="attach-directly-to-a-program"></a>Asociar directamente a un programa
Los usuarios que desean depurar programas en un proceso que ya se está ejecutando normalmente siguen este proceso:  
  
1.  En el IDE, elija el **procesos de depuración** comando desde el **herramientas** menú.  
  
     Aparecerá el cuadro de diálogo **Procesos**.  
  
2.  Elegir un proceso y haga clic en el **adjuntar** botón.  
  
     El **asociar al proceso** aparece el cuadro de diálogo lista de todos los motores de depuración (DEs) instalados en el equipo.  
  
3.  Especifique el DEs a usar para depurar el proceso seleccionado y, a continuación, haga clic en **Aceptar**.  
  
 El paquete de depuración inicia una sesión de depuración y le pasa la lista de DEs. La sesión de depuración a su vez pasa esta lista, junto con una función de devolución de llamada para el proceso seleccionado y, a continuación, solicita el proceso para enumerar sus programas en ejecución.  
  
 Mediante programación, en respuesta a la solicitud del usuario, el paquete de depuración crea una instancia del Administrador de depuración de la sesión (SDM) y le pasa la lista de DEs seleccionado. Junto con la lista, el paquete de depuración pasa el SDM un [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interfaz. El paquete de depuración pasa la lista de DEs para el proceso seleccionado mediante una llamada a [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). A continuación, llama el SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) en el puerto para enumerar los programas que se ejecutan en el proceso.  
  
 Desde este punto, cada motor de depuración se adjunta a un programa exactamente como se detalla en [asociar después de un lanzamiento](../../extensibility/debugger/attaching-after-a-launch.md), con dos excepciones.  
  
 Para mejorar la eficacia, DEs que se implementan para compartir un espacio de direcciones con el SDM se agrupan para que cada DE tiene un conjunto de programas se asociará. En este caso, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) llamadas [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) y lo pasa una matriz de programas para adjuntar a.  
  
 La segunda excepción es que los eventos de inicio enviados por una DE asociación a un programa que ya se está ejecutando normalmente no incluyen el evento de punto de entrada.  
  
## <a name="see-also"></a>Vea también  
 [Envío de eventos de inicio después de un lanzamiento](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)