---
title: "IDebugCoreServer3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3"
helpviewer_keywords: 
  - "Interfaz IDebugCoreServer3"
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz proporciona acceso a información sobre el servidor que el proceso se está ejecutando en.  
  
## Sintaxis  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## Notas para los implementadores  
 Visual Studio implementa esta interfaz.  
  
## Notas para los llamadores  
 uso [QueryInterface](/visual-cpp/atl/queryinterface) de obtener esta interfaz de una interfaz de [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) .  Una llamada a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) también puede devolver esta interfaz.  Esta interfaz se utiliza con más frecuencia por un proveedor de puerto para iniciar los programas del servidor \(local o remoto\).  
  
## métodos en el orden de Vtable  
 Además de los métodos de la interfaz de [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Recupera el nombre del servidor.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Recupere una versión descriptiva de nombre de servidor|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indica los motores específicos de depuración automáticamente al envío a procesos cuando esos procesos empiezan.|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Recupera un código de error específico cuando la asociación automática.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Crea una instancia de un motor de depuración en el servidor.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Recupera una marca que indica si el servidor está en el mismo equipo que el llamador.|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Recupera un valor que indica el protocolo que se usa para comunicarse con el servidor.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Deshabilita todos los valores de la asociación automática para todos los motores de depuración que este servidor tiene información.|  
  
## Comentarios  
 Un proveedor de puerto recibe la interfaz de [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) en una llamada a [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md).  La interfaz de `IDebugCoreServer3` se puede obtener de la interfaz.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)