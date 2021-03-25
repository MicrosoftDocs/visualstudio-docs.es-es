---
description: Esta interfaz permite al administrador de depuración de sesión (SDM) asociar a un programa y obtener el nodo de programa asociado a un programa.
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e39a469d04ac14f3ed36366d035bf4ca01a9d2ef
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087332"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
Esta interfaz permite al administrador de depuración de sesión (SDM) asociar a un programa y obtener el nodo de programa asociado a un programa.

## <a name="syntax"></a>Sintaxis

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de Puerto personalizado implementa esta interfaz en el mismo objeto que la interfaz [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) para permitir que el SDM se asocie a un programa al mismo tiempo que permite al proveedor del puerto realizar un seguimiento de todas las sesiones asociadas al programa. El proveedor del puerto personalizado puede implementar esta interfaz si elige.

## <a name="notes-for-callers"></a>Notas para llamadores
 El SDM llama a [QueryInterface](/cpp/atl/queryinterface) en una `IDebugProgram2` interfaz para obtener esta interfaz y realizar el seguimiento de las sesiones que se han adjuntado a programas.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugProgramEx2` .

|Método|Descripción|
|------------|-----------------|
|[Adjuntar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Adjunta un programa a una sesión.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtiene el nodo de programa asociado a un programa.|

## <a name="remarks"></a>Observaciones
 Esta interfaz es privada entre el SDM y el programa.

## <a name="requirements"></a>Requisitos
 Encabezado: Portpriv. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
