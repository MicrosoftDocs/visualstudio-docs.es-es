---
description: Esta interfaz enumera los procesos que se ejecutan en un puerto de depuración.
title: IEnumDebugProcesses2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1272c57b58b4e2656775bf746d470a3514c886ea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064545"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Esta interfaz enumera los procesos que se ejecutan en un puerto de depuración.

## <a name="syntax"></a>Sintaxis

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de Puerto personalizado implementa esta interfaz para proporcionar una lista de los procesos que se ejecutan en un puerto.

## <a name="notes-for-callers"></a>Notas para llamadores
 Visual Studio llama a [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) para obtener esta interfaz.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IEnumDebugProcesses2` .

|Método|Descripción|
|------------|-----------------|
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Recupera un número especificado de procesos en una secuencia de enumeración.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Omite un número especificado de procesos en una secuencia de enumeración.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Restablece una secuencia de enumeración al principio.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Crea un enumerador que contiene el mismo estado de enumeración que el enumerador actual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Obtiene el número de procesos de un enumerador.|

## <a name="remarks"></a>Observaciones
 Visual Studio usa esta interfaz para rellenar la ventana **procesos** .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
