---
title: IDebugCoreServer2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce3e4c0c933527a5db754dcd96de97283e6e8260
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Esta interfaz se usa para representar y obtener información de un servidor en un equipo en la red.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Visual Studio implementa esta interfaz para representar un servidor. Cada instancia de Visual Studio crea una instancia de esta interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Un proveedor de puerto personalizado recibe esta interfaz en una llamada a [eventos](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Un motor de depuración puede obtener esta interfaz indirectamente a través de una llamada a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (que devuelve [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), una interfaz que se deriva de `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugCoreServer2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Obtiene el nombre y atributos de una máquina.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Obtiene el nombre de una máquina.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Obtiene un proveedor de puerto que existe en un equipo.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Obtiene un puerto que ya existe en un equipo.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Crea un enumerador para todos los puertos en un equipo.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Crea un enumerador para todos los proveedores de puerto en un equipo.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Obtiene las utilidades de máquina de una máquina.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz también se usa Visual Studio para examinar los procesos que se ejecutan en equipos de la red.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)