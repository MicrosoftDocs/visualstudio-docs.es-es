---
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 629e35e8756be1dfa6df9f21eda02624b4c363de
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691324"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Esta interfaz proporciona acceso a información sobre el servidor en que se está ejecutando el proceso.

## <a name="syntax"></a>Sintaxis

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Visual Studio implementa esta interfaz.

## <a name="notes-for-callers"></a>Notas para los llamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obtener esta interfaz desde una [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaz. Una llamada a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) también se puede devolver esta interfaz. Esta interfaz se usa con mayor frecuencia por un proveedor de puerto personalizado para iniciar programas en un servidor (local o remoto).

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
 Además de los métodos en el [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaz, esta interfaz implementa los métodos siguientes:

|Método|Descripción|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Recupera el nombre del servidor.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Recupera una versión descriptiva del nombre del servidor|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indica los motores de depuración específicos para adjuntar automáticamente a los procesos al inician los procesos.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Recupera un código de error específico al adjuntar de automático se produce un error.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Crea una instancia de un motor de depuración en el servidor.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Recupera una marca que indica si el servidor está en la misma máquina que el llamador.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Recupera un valor que indica el protocolo que se usa para comunicarse con el servidor.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Deshabilita todos los asociar automáticamente la configuración para todos los motores de depuración que conoce este servidor.|

## <a name="remarks"></a>Comentarios
 Un proveedor de puerto personalizado recibe el [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaz en una llamada a [eventos](../../../extensibility/debugger/reference/idebugportevents2-event.md). El `IDebugCoreServer3` interfaz puede obtenerse a partir de esa interfaz.

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)