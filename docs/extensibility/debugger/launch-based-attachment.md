---
title: Datos adjuntos basada en Inicio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 892518cc92286f9415e39c96b6ed2afa8eb0d792
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099381"
---
# <a name="launch-based-attachment"></a>Datos adjuntos basada en Inicio
Datos adjuntos en función de inicio a un programa son automático. Cuando se inicia el proceso que hospeda el programa envía el SDM, datos adjuntos basada en Inicio siguen una ruta de acceso similar a la que el método de conexión manual. Para obtener información, consulte [asociar al programa](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>El proceso de asociación  
 La diferencia principal es la secuencia de eventos después de la **adjuntar** llamar, como se indica a continuación:  
  
1.  Enviar una **IDebugEngineCreateEvent2** objeto de evento para el SDM. Para obtener más información, consulte [enviar eventos](../../extensibility/debugger/sending-events.md).  
  
2.  Llame a la `IDebugProgram2::GetProgramId` método en el **IDebugProgram2** interfaz se pasa a la **adjuntar** método.  
  
3.  Enviar una **IDebugProgramCreateEvent2** objeto de evento para notificar el SDM que la variable local **IDebugProgram2** objeto se creó para representar el sistema a la DE.  
  
4.  Enviar una [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) objeto de evento para notificar el SDM que se crea un nuevo subproceso para el proceso que se inicia.  
  
## <a name="see-also"></a>Vea también  
 [Enviar los eventos necesarios](../../extensibility/debugger/sending-the-required-events.md)   
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)