---
title: IDebugProviderProgramNode2 | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33c4a4914e15a8ecbea0d4f28c2325a952a042de
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353802"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Esta interfaz calcula las referencias de las interfaces relacionadas con el programa a través de los límites del proceso.

## <a name="syntax"></a>Sintaxis

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor de depuración (DE) implementa esta interfaz en el mismo objeto que implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para admitir la serialización de interfaces en los límites del proceso.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Llame a [QueryInterface](/cpp/atl/queryinterface) en un `IDebugProgramNode2` interfaz para obtener esta interfaz. Si no se puede obtener esta interfaz, la DE no admite el cálculo de referencias de interfaces.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Obtiene una interfaz especificada a través de los límites del proceso.|

## <a name="remarks"></a>Comentarios
 Esta interfaz se implementa cuando se ejecuta la DE en un espacio de proceso independiente desde el programa que se está depurando: por ejemplo, cuando se ejecuta la DE en el espacio de procesos de Visual Studio en lugar del espacio de proceso del programa que se está depurando.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)