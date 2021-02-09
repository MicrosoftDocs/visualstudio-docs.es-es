---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d22a58021a744cc71b8df3acb8e577d853aa2829
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889998"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Esta interfaz representa un programa que se ejecuta en un proceso y extiende la [ejecución](../../../extensibility/debugger/reference/idebugprogram2-execute.md) proporcionando información de subprocesos.

## <a name="syntax"></a>Sintaxis

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) y un proveedor de Puerto personalizado implementan esta interfaz para representar un programa en un proceso. El administrador de depuración de sesión (SDM) también implementa esta interfaz para proporcionar la información que se va a [adjuntar](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Notas para llamadores
 El evento [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) devuelve esta interfaz para un nuevo programa. Esta interfaz también se utiliza como parámetro para muchos métodos en varias interfaces.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugProgram3` .

|Método|Descripción|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Ejecuta el programa. El subproceso se devuelve para proporcionar a la información del depurador el subproceso que el usuario está viendo cuando se ejecuta.|

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Notas
 Un programa es un contenedor de subprocesos que se ejecuta en una arquitectura en tiempo de ejecución determinada, mientras que un proceso se compone de uno o varios programas.

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Siguiente](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
