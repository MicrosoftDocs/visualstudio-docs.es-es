---
title: "IDebugProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2"
helpviewer_keywords: 
  - "Interfaz IDebugProgram2"
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un programa que se ejecuta en un proceso.  
  
## Sintaxis  
  
```  
IDebugProgram2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) y un proveedor de puerto implementan esta interfaz para representar un programa en un proceso.  El administrador de depuración de la sesión \(SDM\) también implementa esta interfaz para proporcionar información a [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md).  
  
## Notas para los llamadores  
 el evento de [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) devuelve esta interfaz para un nuevo programa.  Esta interfaz también se utiliza como parámetro para muchos métodos en varias interfaces.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugProgram2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Enumera los subprocesos que se ejecutan en este programa.|  
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Obtiene el nombre del programa.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Obtiene el proceso que este programa ejecuta en.|  
|[Terminar](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|finaliza este programa.|  
|[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Asociado a este programa.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Determina si un motor de depuración \(DE\) puede desasociarse del programa.|  
|[Desasociar](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Desasocia el depurador de este programa.|  
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|obtiene un identificador único global para este programa.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Obtiene las propiedades del programa.|  
|[Ejecutar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Sigue ejecutando este programa de un estado detenido.  Borre cualquier estado anterior de la ejecución.|  
|[Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Sigue ejecutando este programa de un estado detenido.  Conservar cualquier estado anterior de la ejecución.|  
|[Paso](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Realiza un paso.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Las solicitudes que este programa detiene la ejecución la próxima vez uno de los subprocesos ejecutan código.|  
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Obtiene el nombre y el identificador del motor \(DE\) de depuración que ejecuta este programa.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Enumera los contextos de código para una posición determinada de un archivo de código fuente.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|obtiene los bytes de memoria para este programa.|  
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Obtiene el desensamblado transmitir para este programa o parte del programa.|  
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Enumera módulos que este programa ha cargado y se está ejecutando.|  
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Obtiene la opción editar y continuar \(ENC\) actualizados para este programa.<br /><br /> Un motor de depuración no implementa este método \(siempre debe devolver `E_NOTIMPL`\).|  
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Muestra las rutas de acceso del código de este programa.|  
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Escribe un volcado en un archivo.|  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Comentarios  
 Un programa es una ejecución del contenedor en una arquitectura determinada en tiempo de ejecución, mientras que un proceso consta de uno o más programas.  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)