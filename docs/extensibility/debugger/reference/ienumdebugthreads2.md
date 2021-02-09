---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e3771545d4a5fe545382344d17ed5ea929999d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852783"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Esta interfaz enumera los subprocesos que se ejecutan en la sesión de depuración actual.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para representar una lista de subprocesos de un programa.

## <a name="notes-for-callers"></a>Notas para llamadores
 Llame a [enumthreads (](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) para obtener esta interfaz que representa una lista de todos los subprocesos de todos los programas que se ejecutan en un proceso. Llame a [enumthreads (](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) para obtener esta interfaz que representa una lista de subprocesos que se ejecutan en un programa.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IEnumDebugThreads2` .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Recupera un número especificado de subprocesos en la secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Omite un número especificado de subprocesos en una secuencia de enumeración.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Obtiene el número de subprocesos de un enumerador.|

## <a name="remarks"></a>Notas
 Normalmente, Visual Studio obtiene esta interfaz para actualizar la ventana **subprocesos** , así como para obtener el primer subproceso de la lista, con el fin de llamar a [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)y [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Ejecutar](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
