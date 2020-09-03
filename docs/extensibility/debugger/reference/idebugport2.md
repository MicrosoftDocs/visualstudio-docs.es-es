---
title: IDebugPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62912be9fdfecc98a264a58c9713cc12ccaf28f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725232"
---
# <a name="idebugport2"></a>IDebugPort2
Esta interfaz representa un puerto de depuración en un equipo.

## <a name="syntax"></a>Sintaxis

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Un proveedor de Puerto personalizado implementa esta interfaz para representar un puerto de depuración en un equipo.

 Si el puerto admite el envío de eventos de puerto, también debe implementar la <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfaz para admitir una <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfaz que, a su vez, proporciona la interfaz [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .

## <a name="notes-for-callers"></a>Notas para llamadores
 Las llamadas a [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) o [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) devuelven esta interfaz, que representa el puerto solicitado.

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 En la tabla siguiente se muestran los métodos de `IDebugPort2` .

|Método|Descripción|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Devuelve el nombre del puerto.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Devuelve el identificador de puerto.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Devuelve la solicitud utilizada para crear un puerto (si está disponible).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Devuelve el proveedor del puerto para este puerto.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Devuelve una interfaz al proceso dado el identificador del proceso.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Enumera todos los procesos que se ejecutan en un puerto.|

## <a name="remarks"></a>Observaciones
 El puerto local proporciona acceso a todos los procesos y programas que se ejecutan en el equipo local. Otros puertos pueden representar una conexión de cable serie a un dispositivo basado en Windows CE o una conexión de red a un equipo no DCOM. La `IDebugPort2` interfaz se utiliza para buscar el nombre y el identificador de un puerto y enumerar todos los procesos que se ejecutan en el puerto. En la interfaz se implementan los recursos para iniciar y terminar los procesos en el puerto `IDebugPortEx2` .

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Interfaces básicas](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
