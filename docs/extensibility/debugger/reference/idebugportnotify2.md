---
description: Esta interfaz registra o anula el registro de un programa que se puede depurar con el puerto en el que se está ejecutando.
title: IDebugPortNotify2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4000426b72472d57b589f26543dd1547f8dc982
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072395"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Esta interfaz registra o anula el registro de un programa que se puede depurar con el puerto en el que se está ejecutando.

## <a name="syntax"></a>Sintaxis

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de Puerto personalizado implementa esta interfaz para admitir la adición y eliminación de programas desde el puerto. Normalmente se implementa en el mismo objeto que implementa la interfaz [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) .

## <a name="notes-for-callers"></a>Notas para llamadores
 Una llamada a [QueryInterface](/cpp/atl/queryinterface) en la `IDebugPort2` interfaz devuelve esta interfaz. Además, una llamada a [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) devuelve esta interfaz. Un motor de depuración puede ver esta interfaz como un parámetro de [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugPortNotify2` .

|Método|Descripción|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra un programa que se puede depurar con el puerto en el que se está ejecutando.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Anula el registro de un programa que se puede depurar desde el puerto en el que se está ejecutando.|

## <a name="remarks"></a>Observaciones
 A menos que un puerto de depuración tenga una manera de saber cuándo se cargan o descargan programas, un proveedor de Puerto personalizado debe implementar esta interfaz. Se realiza un seguimiento de todos los programas que se cargan para la depuración a través de un puerto determinado mediante esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
