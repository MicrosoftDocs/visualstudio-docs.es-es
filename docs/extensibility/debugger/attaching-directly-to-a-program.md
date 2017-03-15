---
title: "Asociar directamente a un programa | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motores de depuración, asociar a programas"
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Asociar directamente a un programa
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los usuarios que desean a los programas de depuración en un proceso que está ejecutando normalmente siguen este proceso:  
  
1.  En el IDE, elija el comando de **Procesos de depuración** de menú de **Herramientas** .  
  
     Aparecerá el cuadro de diálogo **Procesos**.  
  
2.  Elija un proceso y haga clic en el botón de **Asociar** .  
  
     El cuadro de diálogo de **Adjuntar a procesar** aparece, enumerando todos los motores \(DEs\) de depuración instalados en el equipo.  
  
3.  Especifique el DES para utilizar para depurar el proceso seleccionado, haga clic en **Aceptar**.  
  
 El paquete de depuración inicia una sesión de depuración y pasa la lista de a.  La sesión de depuración a su vez pasa esta lista, junto con una función de devolución de llamada, el proceso seleccionado, y se pide el proceso para enumerar los programas en ejecución.  
  
 Mediante programación, en respuesta a la solicitud de usuario, el paquete de depuración crea una instancia del administrador \(SDM\) de depuración de la sesión y pasa la lista de DES seleccionados a.  Junto con la lista, el paquete de depuración pasa el SDM una interfaz de [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) .  El paquete de depuración pasa la lista de el proceso seleccionado llamando a [IDebugProcess2:: Asociar](../../extensibility/debugger/reference/idebugprocess2-attach.md).  El SDM llama [IDebugProcess2:: EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) en el puerto para enumerar los programas que se ejecutan en el proceso.  
  
 Desde aquí, cada motor de depuración está asociado a un programa exactamente como se detalla en [Asociar Después una versión](../../extensibility/debugger/attaching-after-a-launch.md), con dos excepciones.  
  
 Para aumentar la eficacia, el DES que se implementan para compartir un espacio de direcciones con el SDM se agrupa de forma que cada OF tiene un conjunto de programas se adjuntará a.  En este caso, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) llama [IDebugEngine2:: Asociar](../../extensibility/debugger/reference/idebugengine2-attach.md) y se le pasa una matriz de programas a la asociación a.  
  
 La segunda excepción es que los eventos de inicio enviados por un OF que asocia un programa que se está ejecutando no incluyen normalmente el evento de punto de entrada.  
  
## Vea también  
 [Enviar eventos de inicio después de un lanzamiento](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)