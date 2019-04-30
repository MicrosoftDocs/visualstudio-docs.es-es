---
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c127bdb807b397060342bf7051c3c0de1251627f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62569228"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz proporciona acceso a información sobre el servidor en que se está ejecutando el proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Visual Studio implementa esta interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Use [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para obtener esta interfaz desde una [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interfaz. Una llamada a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) también se puede devolver esta interfaz. Esta interfaz se usa con mayor frecuencia por un proveedor de puerto personalizado para iniciar programas en un servidor (local o remoto).  
  
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
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
