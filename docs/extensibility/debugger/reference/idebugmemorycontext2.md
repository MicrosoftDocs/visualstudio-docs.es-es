---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727428"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Esta interfaz representa una posición en el espacio de direcciones de la máquina que ejecuta el programa que se está depurando.

## <a name="syntax"></a>Sintaxis

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor DE depuración (DE) implementa esta interfaz para representar una dirección en memoria.

## <a name="notes-for-callers"></a>Notas para llamadores
 Una llamada a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) o [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) devuelve esta interfaz. Además, las llamadas a [sumar](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) y [restar](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) devuelven nuevas copias de esta interfaz después de aplicar la operación aritmética adecuada.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugMemoryContext2` .

|Método|Descripción|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Obtiene el nombre de usuario que se pueda mostrar para este contexto.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Obtiene información que describe este contexto.|
|[Add (Agregar)](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Agrega un valor especificado a la dirección del contexto actual para crear un nuevo contexto.|
|[Restar](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Resta un valor especificado de la dirección del contexto actual para crear un nuevo contexto.|
|[Comparar](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Compara dos contextos de la manera indicada por las marcas de comparación.|

## <a name="remarks"></a>Observaciones
 La ventana **memoria** de Visual Studio llama a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) para obtener la `IDebugMemoryContext2` interfaz que contiene la expresión evaluada que se usa para la dirección de memoria. A continuación, este contexto se pasa a [readatum](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) y [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) para especificar la dirección que se va a leer o escribir.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
