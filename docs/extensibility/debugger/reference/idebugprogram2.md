---
description: Esta interfaz representa un programa que se ejecuta en un proceso.
title: IDebugProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2f6effa250749f448ed1a02c4b7a699d50b7388e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105084407"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Esta interfaz representa un programa que se ejecuta en un proceso.

## <a name="syntax"></a>Sintaxis

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) y un proveedor de Puerto personalizado implementan esta interfaz para representar un programa en un proceso. El administrador de depuración de sesión (SDM) también implementa esta interfaz para proporcionar la información que se va a [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Notas para llamadores
 El evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) devuelve esta interfaz para un nuevo programa. Esta interfaz también se utiliza como parámetro para muchos métodos en varias interfaces.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugProgram2` .

|Método|Descripción|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Enumera los subprocesos que se están ejecutando en este programa.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Obtiene el nombre del programa.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Obtiene el proceso en el que se está ejecutando este programa.|
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Finaliza este programa.|
|[Adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Se adjunta a este programa.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Determina si un motor de depuración (DE) se puede desasociar del programa.|
|[Separar](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Desasocia el depurador de este programa.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Obtiene un identificador único global para este programa.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Obtiene las propiedades del programa.|
|[Ejecutar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Sigue ejecutando este programa desde un estado detenido. Se borra cualquier estado de ejecución anterior.|
|[Continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Sigue ejecutando este programa desde un estado detenido. Se conserva cualquier estado de ejecución anterior.|
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Realiza un paso.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Solicita que este programa detenga la ejecución la próxima vez que uno de sus subprocesos ejecute código.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Obtiene el nombre y el identificador del motor de depuración (DE) que ejecuta este programa.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Enumera los contextos de código para una posición determinada en un archivo de código fuente.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Obtiene los bytes de memoria para este programa.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Obtiene la secuencia de desensamblado para este programa o parte de este programa.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Enumera los módulos que este programa ha cargado y se está ejecutando.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Obtiene la actualización de editar y continuar (ENC) para este programa.<br /><br /> Un motor de depuración personalizado no implementa este método (siempre debe devolver `E_NOTIMPL` ).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Enumera las rutas de acceso del código de este programa.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Escribe un volcado en un archivo.|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Observaciones
 Un programa es un contenedor de subprocesos que se ejecuta en una arquitectura en tiempo de ejecución determinada, mientras que un proceso se compone de uno o varios programas.

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Siguiente](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
