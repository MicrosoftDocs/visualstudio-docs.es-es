---
description: Esta interfaz calcula las referencias de las interfaces relacionadas con el programa a través de los límites del proceso.
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d09046d70d6bc766d17963ea4cdd6469c0981fb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083679"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Esta interfaz calcula las referencias de las interfaces relacionadas con el programa a través de los límites del proceso.

## <a name="syntax"></a>Sintaxis

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 El motor DE depuración (DE) implementa esta interfaz en el mismo objeto que implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para admitir las interfaces de serialización a través de los límites del proceso.

## <a name="notes-for-callers"></a>Notas para llamadores
 Llame a [QueryInterface](/cpp/atl/queryinterface) en una `IDebugProgramNode2` interfaz para obtener esta interfaz. Si no se puede obtener esta interfaz, el DE no admite el cálculo de referencias de interfaces.

## <a name="methods-in-vtable-order"></a>Métodos en orden vtable
 Esta interfaz implementa el método siguiente:

|Método|Descripción|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Obtiene una interfaz especificada a través de los límites del proceso.|

## <a name="remarks"></a>Observaciones
 Esta interfaz se implementa cuando el DE se ejecuta en un espacio de proceso independiente desde el programa que se está depurando: por ejemplo, cuando el DE se está ejecutando en el espacio de proceso de Visual Studio en lugar de en el espacio de proceso del programa que se está depurando.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
