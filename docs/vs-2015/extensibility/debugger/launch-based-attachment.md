---
title: Adjunto basado en Inicio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3603f14d07eb8531480b89f24d73cbd5045da7c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188313"
---
# <a name="launch-based-attachment"></a>Adjunto basado en el inicio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Basado en el lanzamiento de los datos adjuntos a un programa son automático. Cuando se inicia el proceso que hospeda el programa mediante el SDM, basado en el lanzamiento de los datos adjuntos siguen una ruta de acceso similar a la del método manual de los datos adjuntos. Para obtener información, consulte [asociar al programa](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>El proceso de asociación  
 La diferencia principal es la secuencia de eventos siguiendo el **adjuntar** llamar, como sigue:  
  
1.  Enviar una **IDebugEngineCreateEvent2** objeto event para el SDM. Para obtener más información, consulte [enviar eventos](../../extensibility/debugger/sending-events.md).  
  
2.  Llame a la `IDebugProgram2::GetProgramId` método en el **IDebugProgram2** interfaz se pasa a la **adjuntar** método.  
  
3.  Enviar una **IDebugProgramCreateEvent2** objeto de evento para notificar el SDM que local **IDebugProgram2** objeto se creó para representar el programa a la DE.  
  
4.  Enviar una [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) objeto de evento para notificar el SDM que se crea un nuevo subproceso para el proceso que se inicia.  
  
## <a name="see-also"></a>Vea también  
 [Envío de los eventos necesarios](../../extensibility/debugger/sending-the-required-events.md)   
 [Habilitación de un programa que se desea depurar](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

