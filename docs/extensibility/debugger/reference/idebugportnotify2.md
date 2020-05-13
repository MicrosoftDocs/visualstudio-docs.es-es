---
title: IDebugPortNotify2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d3d1161d488ed4a9e12b7af6b70bf336c9f286
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724916"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Esta interfaz registra o anula el registro de un programa que se puede depurar con el puerto en el que se está ejecutando.

## <a name="syntax"></a>Sintaxis

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de puertos personalizado implementa esta interfaz para admitir la adición y eliminación de programas del puerto. Normalmente se implementa en el mismo objeto que implementa el [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaz.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Una llamada a [QueryInterface](/cpp/atl/queryinterface) en la `IDebugPort2` interfaz devuelve esta interfaz. Además, una llamada a [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) devuelve esta interfaz. Un motor de depuración puede ver esta interfaz como un parámetro de [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugPortNotify2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra un programa que se puede depurar con el puerto en el que se ejecuta.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Anula el registro de un programa que se puede depurar desde el puerto en el que se ejecuta.|

## <a name="remarks"></a>Observaciones
 A menos que un puerto de depuración tenga una manera de saber cuándo se cargan o descargan los programas, un proveedor de puerto personalizado debe implementar esta interfaz. Todos los programas que se cargan para la depuración a través de un puerto determinado se rastrean mediante esta interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
