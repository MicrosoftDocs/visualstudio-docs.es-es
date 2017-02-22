---
title: "IDebugCoreServer2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer2"
helpviewer_keywords: 
  - "Interfaz IDebugCoreServer2"
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz se utiliza para representar y obtener información de un servidor en un equipo de la red.  
  
## Sintaxis  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## Notas para los implementadores  
 Visual Studio implementa esta interfaz para representar un servidor.  cada instancia de Visual Studio crea una instancia de esta interfaz.  
  
## Notas para los llamadores  
 Un proveedor de puerto recibe esta interfaz en una llamada a [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Un motor de depuración puede obtener esta interfaz a una llamada a [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) \(que devuelve [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), una interfaz que es derivada de `IDebugCoreServer2`\).  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugCoreServer2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|obtiene el nombre y los atributos de un equipo.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|obtiene el nombre de un equipo.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Obtiene un proveedor de puerto que reside en un equipo.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Obtiene un puerto que ya existe en un equipo.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Crea un enumerador de todos los puertos en un equipo.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Crea un enumerador de todos los proveedores de puerto en un equipo.|  
|[GetMachineUtilities\_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Obtiene las utilidades de equipo para un equipo.|  
  
## Comentarios  
 Esta interfaz también usa Visual Studio para examinar los procesos que se ejecutan en equipos de la red.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)