---
title: IDebugCoreServer2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5990c84fbaeb5ebb3b1e188d3317234afda06b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733020"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Esta interfaz se utiliza para representar y obtener información de un servidor en una máquina de la red.

## <a name="syntax"></a>Sintaxis

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio implementa esta interfaz para representar un servidor. Cada instancia de Visual Studio crea una instancia de esta interfaz.

## <a name="notes-for-callers"></a>Notas para las personas que llaman
 Un proveedor de puerto personalizado recibe esta interfaz en una llamada a [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md).

 Un motor de depuración puede obtener esta interfaz indirectamente a través de una llamada `IDebugCoreServer2`a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (que devuelve [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), una interfaz que se deriva de ).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente `IDebugCoreServer2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Obtiene el nombre y los atributos de una máquina.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Obtiene el nombre de una máquina.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Obtiene un proveedor de puertos que existe en una máquina.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Obtiene un puerto que ya existe en una máquina.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Crea un enumerador para todos los puertos de una máquina.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Crea un enumerador para todos los proveedores de puertos de una máquina.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Obtiene las utilidades de la máquina para una máquina.|

## <a name="remarks"></a>Observaciones
 Visual Studio también usa esta interfaz para examinar los procesos que se ejecutan en equipos de la red.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
