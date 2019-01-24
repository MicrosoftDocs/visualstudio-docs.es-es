---
title: IDebugEngine2 | Documentos de Microsoft
ms.date: 11/04/2016
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
ms.openlocfilehash: 384d6179f2e8a8c9252e4c631a97d8e429330f96
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914228"
---
# <a name="idebugengine2"></a>IDebugEngine2
Esta interfaz representa un motor de depuración (DE). Sirve para administrar diversos aspectos de una sesión de depuración, desde la creación de puntos de interrupción para establecer y borrar las excepciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante una DE personalizado para administrar la depuración de programas. Esta interfaz debe implementarse mediante la DE.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El Administrador de depuración (SDM) para administrar la sesión de depuración, incluidos administración de excepciones, creación de puntos de interrupción y responder a eventos sincrónicos enviados por la DE sesión llama a esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugEngine2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crea un enumerador para todos los programas que se está depurando mediante una DE.|  
|[Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Asocia un DE a un programa.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crea un punto de interrupción pendiente en la DE.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Especifica la forma en que la DE debe controlar una excepción determinada.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Borra la excepción especificada para que ya no es controlada por el motor de depuración.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Quita la lista de excepciones que se estableció el IDE para una determinada arquitectura en tiempo de ejecución o lenguaje.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Obtiene el GUID de la DE.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa a DE que el programa especificado se ha terminado atypically y que debería limpiar todas las referencias al programa y enviar un programa de la DE evento de destrucción.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Lo llama el SDM para indicar que un evento de depuración sincrónica, enviado anteriormente por la DE para el SDM, se ha recibido y procesado.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Establece la configuración regional de la DE.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Establece la raíz del registro actualmente en uso por la DE.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Establece una métrica.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Solicitudes que todos los programas que se está depurados por esta DE detener la ejecución de la próxima vez que uno de sus subprocesos intenta ejecutar.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)