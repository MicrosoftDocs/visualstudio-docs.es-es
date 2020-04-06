---
title: IDebugMemoryBytes2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56cb234e2295c5c9c08c2a2e9271e1c173524875
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727505"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Esta interfaz representa bytes de memoria.

## <a name="syntax"></a>Sintaxis

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz para representar bytes en memoria.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) devuelve esta interfaz para proporcionar acceso a la memoria del sistema. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) y [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) devuelven esta interfaz para proporcionar acceso a los bytes de un objeto.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugMemoryBytes2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Lee una secuencia de bytes, comenzando en una ubicación determinada.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Escribe `dwCount` bytes, empezando por `pStartContext`.|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Obtiene el tamaño, en bytes, de la memoria representada por esta interfaz.|

## <a name="remarks"></a>Observaciones
 Para las propiedades, un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) `IDebugMemoryBytes2` interfaz que representa una matriz proporciona una interfaz para tener acceso a los valores de esa matriz.

 Vista de **memoria** de Visual Studio llama `IDebugMemoryBytes2` a [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) para recuperar una interfaz para tener acceso a la memoria del sistema. La dirección a la que se va a tener acceso se obtiene analizando la expresión introducida como dirección `IDebugProperty2` en la vista de memoria y, a continuación, evaluando la expresión analizada mediante [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obtener una interfaz. Una llamada a [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) devuelve el [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que describe la dirección de memoria. A continuación, este contexto de memoria se pasa a [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) y [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
