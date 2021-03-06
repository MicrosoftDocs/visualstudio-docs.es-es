---
description: Esta interfaz representa un motor DE depuración (DE).
title: IDebugEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6e32c4798ad1bea65a9aadcf8a0d73052acc238
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066157"
---
# <a name="idebugengine2"></a>IDebugEngine2
Esta interfaz representa un motor DE depuración (DE). Se utiliza para administrar diversos aspectos de una sesión de depuración, desde la creación de puntos de interrupción hasta la configuración y el borrado de excepciones.

## <a name="syntax"></a>Sintaxis

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se implementa mediante un personalizado DE para administrar la depuración de programas. El DE debe implementar esta interfaz.

## <a name="notes-for-callers"></a>Notas para llamadores
 El administrador de depuración de la sesión (SDM) llama a esta interfaz para administrar la sesión de depuración, incluida la administración DE excepciones, la creación de puntos de interrupción y la respuesta a eventos sincrónicos enviados por el DE.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugEngine2` .

|Método|Descripción|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crea un enumerador para todos los programas depurados por un DE.|
|[Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Adjunta un DE a un programa.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crea un punto de interrupción pendiente en el DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Especifica cómo debe controlarse el control DE una excepción determinada.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Quita la excepción especificada para que el motor de depuración ya no la administre.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Quita la lista de excepciones que el IDE ha establecido para un idioma o una arquitectura en tiempo de ejecución determinados.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Obtiene el GUID del de.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa a un DE que el programa especificado ha finalizado de forma atípica y que el DE debe limpiar todas las referencias al programa y enviar un evento DE destrucción de programas.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|El SDM llama a este método para indicar que se ha recibido y procesado un evento DE depuración sincrónico, enviado previamente por el DE a SDM.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Establece la configuración regional del de.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Establece la raíz del registro actualmente en uso por parte de.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Establece una métrica.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Solicita que se detenga la ejecución de todos los programas depurados por este DE detención la próxima vez que uno de los subprocesos intente ejecutarse.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
