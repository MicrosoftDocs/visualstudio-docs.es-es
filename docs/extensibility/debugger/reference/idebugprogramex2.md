---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99b57aece9b835ac1f2277fdd626a9fdff7b903f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705104"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Esta interfaz permite que la sesión de depuración manager (SDM) asociar a un programa y obtener el nodo de programa asociado con un programa.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de puerto personalizado implementa esta interfaz en el mismo objeto que el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz para permitir que el SDM asociar a un programa mientras al mismo tiempo, lo que permite el proveedor del puerto realizar el seguimiento de todas las sesiones conectado a la programa. El proveedor del puerto personalizado puede implementar esta interfaz si así lo decide.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Las llamadas SDM [QueryInterface](/cpp/atl/queryinterface) en un `IDebugProgram2` interfaz para obtener esta interfaz para realizar un seguimiento de las sesiones que se han asociado a programas.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 La tabla siguiente muestran los métodos de `IDebugProgramEx2`.

|Método|Descripción|
|------------|-----------------|
|[Asociar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Un programa se asocia a una sesión.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtiene el nodo de programa asociado con un programa.|

## <a name="remarks"></a>Comentarios
 Esta interfaz es privada entre el SDM y el programa.

## <a name="requirements"></a>Requisitos
 Encabezado: Portpriv.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)