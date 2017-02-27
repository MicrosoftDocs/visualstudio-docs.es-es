---
title: "IDebugProcess2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2"
helpviewer_keywords: 
  - "Interfaz IDebugProcess2"
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# IDebugProcess2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un proceso en un puerto.  Si el puerto es el puerto local, después `IDebugProcess2` representa normalmente un proceso físico en el equipo local.  
  
## Sintaxis  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## Notas para los implementadores  
 Esta interfaz se implementa por un proveedor de puerto para administrar programas como grupo.  Esta interfaz se debe implementar el proveedor de puerto.  
  
 Un motor de depuración también implementa esta interfaz si admite iniciar un programa con [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## Notas para los llamadores  
 Esta interfaz es denominada principalmente por el administrador de depuración de la sesión \(SDM\) para interactuar con un grupo de software identificados en este proceso.  
  
 Llame a [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) o [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) para obtener esta interfaz.  Esta interfaz también devuelve llamando a `IDebugEngineLaunch2::LaunchSuspended`.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugProcess2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Obtiene una descripción del proceso.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera los programas incluidos en este proceso.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Obtiene el título, el nombre descriptivo, o el nombre de archivo del proceso.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Obtiene la instancia de un servidor del equipo que este proceso se ejecuta.|  
|[Terminar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|finaliza el proceso.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Asocia el proceso.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|determina si el SDM puede desasociar el proceso.|  
|[Desasociar](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Desasocia el depurador de proceso.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Obtiene el identificador de proceso del sistema.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|obtiene un identificador único global para este proceso.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> \[DEJADO OF UTILIZAR\]|obtiene el nombre de la sesión que está depurando el proceso.<br /><br /> \[DEJADO OF UTILIZAR.  RETORNO `E_NOTIMPL`de SHOULD ALWAYS.\]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|enumera los subprocesos que se ejecutan en el proceso.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Solicitudes que el código en el programa siguiente en esta deje de proceso.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Obtiene el puerto que este proceso se está ejecutando.|  
  
## Comentarios  
 `IDebugProcess2` contiene una o más interfaces de [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)