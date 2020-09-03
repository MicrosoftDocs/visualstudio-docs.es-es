---
title: Iniciar el depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e9c57079246dd52bd7fb44371999d0c3747dad40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149124"
---
# <a name="launching-the-debugger"></a>Inicio del depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Iniciar el depurador requiere el envío de la secuencia correcta de métodos y eventos con sus atributos adecuados.  
  
## <a name="sequences-of-methods-and-events"></a>Secuencias de métodos y eventos  
  
1. Se llama al administrador de depuración de sesión (SDM) eligiendo el menú **depurar** y, a continuación, eligiendo **iniciar**. Vea [iniciar un programa](../../extensibility/debugger/launching-a-program.md) para obtener más información.  
  
2. El SDM llama al método [AutoAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .  
  
3. Según el modelo de proceso del motor DE depuración (DE), el `IDebugProgramNodeAttach2::OnAttach` método devuelve uno de los siguientes métodos, que determina lo que ocurre a continuación.  
  
     Si `S_FALSE` se devuelve, el motor de depuración (de) se cargará en el proceso de la máquina virtual.  
  
     o bien  
  
     Si `S_OK` se devuelve, el de se cargará en proceso del SDM. Después, el SDM realiza las siguientes tareas:  
  
    1. Llama a [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obtener la información del motor de de.  
  
    2. Crea el DE.  
  
    3. Llama a [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4. El DE envía un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) al SDM con un `EVENT_SYNC` atributo.  
  
5. El DE envía un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) al SDM con un `EVENT_SYNC` atributo.  
  
6. El DE envía un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) al SDM con un `EVENT_SYNC` atributo.  
  
7. El DE envía un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) al SDM con un `EVENT_SYNC` atributo.  
  
8. El DE envía un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) al SDM con un `EVENT_SYNC` atributo.  
  
## <a name="see-also"></a>Consulte también  
 [Llamar a eventos del depurador](../../extensibility/debugger/calling-debugger-events.md)   
 [Inicio de un programa](../../extensibility/debugger/launching-a-program.md)
