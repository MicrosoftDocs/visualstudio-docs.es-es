---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1e540d959661a576e211cba526391f852b79a20
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682393"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Esta interfaz representa una posición en el espacio de direcciones de la máquina que ejecuta el programa que se está depurando.

## <a name="syntax"></a>Sintaxis

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para representar una dirección de memoria.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Una llamada a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) o [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) devuelve esta interfaz. Además, las llamadas a [agregar](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) y [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) devolver nuevas copias de esta interfaz se haya aplicado la operación aritmética correspondiente.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugMemoryContext2`.

|Método|Descripción|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Obtiene el nombre de usuario que se puede mostrar para este contexto.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Obtiene la información que describe este contexto.|
|[Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Agrega un valor especificado a la dirección del contexto actual para crear un nuevo contexto.|
|[Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Resta un valor especificado de la dirección del contexto actual para crear un nuevo contexto.|
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Compara dos contextos de la manera indicados por los marcadores de comparación.|

## <a name="remarks"></a>Comentarios
 Visual Studio **memoria** ventana llamadas [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) para obtener el `IDebugMemoryContext2` interfaz que contiene la expresión evaluada que se usa para la dirección de memoria. Este contexto, a continuación, se pasa a [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) y [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) para especificar la dirección para leer o escribir.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)