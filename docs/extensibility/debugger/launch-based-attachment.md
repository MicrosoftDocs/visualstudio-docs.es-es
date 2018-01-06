---
title: Datos adjuntos basada en Inicio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d05f0b8d8fd0190391da831351b65d873eac4efc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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