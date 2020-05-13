---
title: IDebugProviderProgramNode2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720680"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Esta interfaz calcula las referencias de interfaces relacionadas con el programa a través de los límites del proceso.

## <a name="syntax"></a>Sintaxis

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz en el mismo objeto que implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para admitir interfaces de cálculo de referencias a través de los límites del proceso.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Llame a [QueryInterface](/cpp/atl/queryinterface) en una `IDebugProgramNode2` interfaz para obtener esta interfaz. Si esta interfaz no se puede obtener, el DE no soporta el cálculo de referencias de las interfaces.

## <a name="methods-in-vtable-order"></a>Métodos en orden Vtable
 Esta interfaz implementa el siguiente método:

|Método|Descripción|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Obtiene una interfaz especificada a través de los límites del proceso.|

## <a name="remarks"></a>Observaciones
 Esta interfaz se implementa cuando la DE se ejecuta en un espacio de proceso independiente del programa que se está depurando: por ejemplo, cuando la DE se ejecuta en el espacio de proceso de Visual Studio en lugar del espacio de proceso del programa que se está depurando.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
