---
title: IDebugEngine2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e00751db052adeefee828829ec89309a3adba4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730866"
---
# <a name="idebugengine2"></a>IDebugEngine2
Esta interfaz representa un motor de depuración (DE). Se utiliza para administrar varios aspectos de una sesión de depuración, desde la creación de puntos de interrupción hasta la configuración y compensación de excepciones.

## <a name="syntax"></a>Sintaxis

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa mediante un DE personalizado para administrar la depuración de programas. Esta interfaz debe ser implementada por el DE.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 El administrador de depuración de sesión (SDM) llama a esta interfaz para administrar la sesión de depuración, incluida la administración de excepciones, la creación de puntos de interrupción y la respuesta a eventos sincrónicos enviados por la DE.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugEngine2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crea un enumerador para todos los programas que está depurando un DE.|
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Asocia un DE a un programa.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crea un punto de interrupción pendiente en el DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Especifica cómo debe controlar la DE una excepción determinada.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Quita la excepción especificada para que el motor de depuración ya no la controle.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Quita la lista de excepciones que el IDE ha establecido para una arquitectura o lenguaje en tiempo de ejecución determinado.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Obtiene el GUID de la DE.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa a un DE que el programa especificado se ha terminado atípicamente y que el DE debe limpiar todas las referencias al programa y enviar un evento de destrucción del programa.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Llamado por el SDM para indicar que un evento de debug síncrono, enviado previamente por el DE al SDM, fue recibido y procesado.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Establece la configuración regional de la DE.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Establece la raíz del Registro actualmente en uso por la DE.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Establece una métrica.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Solicita que todos los programas depurados por esta DE detengan la ejecución la próxima vez que uno de sus subprocesos intente ejecutarse.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
