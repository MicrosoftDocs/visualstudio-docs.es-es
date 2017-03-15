---
title: "Datos adjuntos basada en el inicio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motores de depuración, iniciar"
  - "motores de depuración, asociar a programas"
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Datos adjuntos basada en el inicio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

los datos adjuntos Lanzamiento\-basados a un programa son automáticos.  Cuando el proceso que hospeda el programa es iniciadas por el SDM, datos adjuntos lanzamiento\-basados siguen una ruta similar a la del método manual de los datos adjuntos.  Para obtener información, vea [Asociar el depurador al programa](../../extensibility/debugger/attaching-to-the-program.md).  
  
## El proceso que asocia  
 La diferencia principal es la secuencia de eventos que realizan la llamada de **Asociar** , como sigue:  
  
1.  Enviar un objeto de evento de **IDebugEngineCreateEvent2** al SDM.  Para obtener información detallada, vea [envío de eventos](../../extensibility/debugger/sending-events.md).  
  
2.  Llame al método de `IDebugProgram2::GetProgramId` en la interfaz de **IDebugProgram2** pasada al método de **Asociar** .  
  
3.  Enviar un objeto de evento de **IDebugProgramCreateEvent2** para notificar al SDM que el objeto local de **IDebugProgram2** se creó para representar el programa se OF.  
  
4.  Enviar un objeto de evento de [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para notificar al SDM que un nuevo subproceso se crea para el proceso que arrancó.  
  
## Vea también  
 [Enviar los eventos necesarios](../../extensibility/debugger/sending-the-required-events.md)   
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)