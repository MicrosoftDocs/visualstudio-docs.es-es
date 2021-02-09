---
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d9d4ee145d900a79a48db44f95a125e87bd10f67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851249"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Esta interfaz representa los bytes de memoria.

## <a name="syntax"></a>Sintaxis

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para representar bytes en memoria.

## <a name="notes-for-callers"></a>Notas para llamadores
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) devuelve esta interfaz para proporcionar acceso a la memoria del sistema. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) y [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) devuelven esta interfaz para proporcionar acceso a los bytes de un objeto.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugMemoryBytes2` .

|Método|Descripción|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Lee una secuencia de bytes, comenzando en una ubicación determinada.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Escribe `dwCount` bytes, a partir de `pStartContext` .|
|[GetSize (](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Obtiene el tamaño, en bytes, de la memoria representada por esta interfaz.|

## <a name="remarks"></a>Notas
 En el caso de las propiedades, una interfaz [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa una matriz proporciona una `IDebugMemoryBytes2` interfaz para tener acceso a los valores de esa matriz.

 La vista de **memoria** de Visual Studio llama a [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) para recuperar una `IDebugMemoryBytes2` interfaz para tener acceso a la memoria del sistema. Se obtiene la dirección a la que se va a obtener acceso mediante el análisis de la expresión especificada como una dirección en la vista de memoria y, a continuación, la evaluación de la expresión analizada mediante [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obtener una `IDebugProperty2` interfaz. Una llamada a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) devuelve el [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que describe la dirección de memoria. A continuación, este contexto de memoria se pasa a [readatum](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) y [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
