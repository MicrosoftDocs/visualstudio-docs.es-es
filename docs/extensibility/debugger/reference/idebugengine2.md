---
title: "IDebugEngine2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2"
helpviewer_keywords: 
  - "Interfaz IDebugEngine2"
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un motor de depuración \(DE\).  Se utiliza para administrar varios aspectos de una sesión de depuración, crear puntos de interrupción a establecer y borrar excepciones.  
  
## Sintaxis  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## Notas para los implementadores  
 Esta interfaz se implementa mediante una personalizada OF para administrar la depuración de software.  Esta interfaz se debe implementar al OF.  
  
## Notas para los llamadores  
 Esta interfaz es denominada por el administrador de depuración de la sesión \(SDM\) para administrar la sesión de depuración, incluso controlar excepciones, crear puntos de interrupción, y la respuesta a los eventos sincrónicos enviados por el OF.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugEngine2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crea un enumerador de todos los programas que se están depurando por un OF.|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Asocia un OF a un programa.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|crea un punto de interrupción pendiente en el DE.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Especifica cómo el OF debe controlar una excepción especificada.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Quita la excepción especificada por lo que controla ya no por el motor de depuración.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Quita la lista de excepciones que el IDE ha establecido para una arquitectura o un lenguaje específica del motor en tiempo de ejecución.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Obtiene el GUID de.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa a un OF que el programa especificado o ha finalizado y que el OF debe limpiar todas las referencias al programa y enviar un programa destruye evento.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Llamado por el SDM para indicar que un evento sincrónico de depuración, incluido previamente por el DE el SDM, se recibió y procesado.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Establece la configuración regional de.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Establece la raíz del registro actualmente en uso en el DE.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Establece una medida.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Las solicitudes que todos los programas que se están depurando por este OF detienen la ejecución la próxima vez uno de los subprocesos intentan ejecutar.|  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)