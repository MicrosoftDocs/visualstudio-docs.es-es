---
title: IDebugEngine2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2cfe7e2f54b45ecfe8fdb34943b87818a13feab
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine2"></a>IDebugEngine2
Esta interfaz representa un motor de depuración (Alemania). Se utiliza para administrar varios aspectos de una sesión de depuración, desde la creación de puntos de interrupción para establecer y borrar las excepciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante un Alemania personalizado para administrar la depuración de programas. Esta interfaz se debe implementar en la DE.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El Administrador de sesión de depuración (SDM) para administrar la sesión de depuración, incluidos administración de excepciones, crear puntos de interrupción y responder a eventos sincrónicos enviados por el DE llama a esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugEngine2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crea un enumerador para todos los programas que está siendo depurado por un Alemania.|  
|[Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Asocia un Alemania a un programa.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crea un punto de interrupción pendiente en el DE.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Especifica cómo el Alemania debe controlar una excepción determinada.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Elimina la excepción especificada para que ya no se administran mediante el motor de depuración.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Quita la lista de excepciones que se estableció el IDE para una determinada arquitectura de tiempo de ejecución o un lenguaje.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Obtiene el GUID de la DE.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa a DE que el programa especificado ha terminado atípicamente y que la DE debe limpiar todas las referencias al programa y enviar un programa destruir eventos.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Lo llama el SDM para indicar que un evento de depuración sincrónico, previamente enviado por el Alemania a SDM, se recibe y procesa.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Establece la configuración regional de la DE.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Establece la raíz del registro actualmente en uso por el DE.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Establece una métrica.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Solicitudes que todos los programas que está siendo depurados por esta DE detener la ejecución la próxima vez que uno de sus subprocesos intenta ejecutar.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)