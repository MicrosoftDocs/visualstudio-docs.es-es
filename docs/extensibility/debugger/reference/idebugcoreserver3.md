---
description: Esta interfaz proporciona acceso a información sobre el servidor en el que se está ejecutando el proceso.
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1328a97742a4672cdc71805c4c674d66fe05e817
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154618"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Esta interfaz proporciona acceso a información sobre el servidor en el que se está ejecutando el proceso.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio implementa esta interfaz.

## <a name="notes-for-callers"></a>Notas para llamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz de una interfaz [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) . Una llamada a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) también puede devolver esta interfaz. Esta interfaz se usa con más frecuencia por un proveedor de Puerto personalizado para iniciar programas en un servidor (ya sea local o remoto).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos de la interfaz [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , esta interfaz implementa los siguientes métodos:

|Método|Descripción|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Recupera el nombre del servidor.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Recupera una versión descriptiva del nombre del servidor.|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indica a los motores de depuración específicos que se adjunten automáticamente a los procesos cuando se inician esos procesos.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Recupera un código de error específico cuando se produce un error al adjuntar automáticamente.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Crea una instancia de un motor de depuración en el servidor.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Recupera una marca que indica si el servidor está en el mismo equipo que el autor de la llamada.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Recupera un valor que indica el protocolo que se utiliza para comunicarse con el servidor.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Deshabilita la configuración de adjuntar automáticamente para todos los motores de depuración que este servidor conoce.|

## <a name="remarks"></a>Observaciones
 Un proveedor de Puerto personalizado recibe la interfaz [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) en una llamada a un [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md). La `IDebugCoreServer3` interfaz se puede obtener a partir de esa interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte también
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
