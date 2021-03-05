---
description: Esta interfaz se usa para representar y obtener información de un servidor en un equipo de la red.
title: IDebugCoreServer2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 871f7ea5671fa4f3c615d84e0591bd331f945ccc
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163140"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Esta interfaz se usa para representar y obtener información de un servidor en un equipo de la red.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio implementa esta interfaz para representar un servidor. Cada instancia de Visual Studio crea una instancia de esta interfaz.

## <a name="notes-for-callers"></a>Notas para llamadores
 Un proveedor de Puerto personalizado recibe esta interfaz en una llamada a un [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md).

 Un motor de depuración puede obtener esta interfaz indirectamente a través de una llamada a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (que devuelve [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), una interfaz que se deriva de `IDebugCoreServer2` ).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugCoreServer2` .

|Método|Descripción|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Obtiene el nombre y los atributos de un equipo.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Obtiene el nombre de un equipo.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Obtiene un proveedor de puerto que existe en un equipo.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Obtiene un puerto que ya existe en un equipo.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Crea un enumerador para todos los puertos de un equipo.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Crea un enumerador para todos los proveedores de puertos en un equipo.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Obtiene las utilidades del equipo para un equipo.|

## <a name="remarks"></a>Observaciones
 Visual Studio también usa esta interfaz para examinar los procesos que se ejecutan en los equipos de la red.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
