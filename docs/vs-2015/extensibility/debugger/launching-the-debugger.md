---
title: Iniciar el depurador | Microsoft Docs
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
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a985d2184ecc69ab4fa2da3b634ab82281fc3ef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201220"
---
# <a name="launching-the-debugger"></a>Inicio del depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Iniciar al depurador requiere el envío de la secuencia correcta de métodos y eventos con sus atributos adecuados.  
  
## <a name="sequences-of-methods-and-events"></a>Secuencias de métodos y eventos  
  
1.  El Administrador de depuración de la sesión (SDM) se denomina eligiendo el **depurar** menú y, a continuación, elija **iniciar**. Consulte [iniciar un programa](../../extensibility/debugger/launching-a-program.md) para obtener más información.  
  
2.  Las llamadas SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método.  
  
3.  Según el modelo de proceso del motor DE depuración, el `IDebugProgramNodeAttach2::OnAttach` método devuelve uno de los métodos siguientes, que determina lo que sucede a continuación.  
  
     Si `S_FALSE` se devuelve, el motor de depuración (DE) es que se cargue en el proceso de la máquina virtual.  
  
     O bien  
  
     Si `S_OK` se devuelve es la DE que se cargue en el proceso del SDM. El SDM, a continuación, realiza las siguientes tareas:  
  
    1.  Las llamadas [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obtener la información del motor de la DE.  
  
    2.  Crea conjuntamente la DE.  
  
    3.  Las llamadas [adjuntar](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  Los envíos DE un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) en el SDM con un `EVENT_SYNC` atributo.  
  
5.  Los envíos DE un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) en el SDM con un `EVENT_SYNC` atributo.  
  
6.  Los envíos DE un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) en el SDM con un `EVENT_SYNC` atributo.  
  
7.  Los envíos DE un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) en el SDM con un `EVENT_SYNC` atributo.  
  
8.  Los envíos DE un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) en el SDM con un `EVENT_SYNC` atributo.  
  
## <a name="see-also"></a>Vea también  
 [Llamar a los eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)   
 [Inicio de un programa](../../extensibility/debugger/launching-a-program.md)

