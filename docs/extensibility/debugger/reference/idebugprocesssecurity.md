---
title: "IDebugProcessSecurity | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugProcessSecurity"
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`IDebugProcessSecurity` se implementa mediante un proveedor de puerto para advertir al usuario que asociar el depurador al proceso es seguro.  
  
## Sintaxis  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugProcessSecurity`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Obtiene el nombre de usuario del proveedor de puerto.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Advierte a un usuario que asociar el depurador al proceso de depuración sea seguro.|  
  
## Comentarios  
 Implemente esta interfaz para mostrar una advertencia y permite al usuario cancelar si el proceso al que está adjuntando puede considerarse no seguro.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Puertos](../../../extensibility/debugger/ports.md)   
 [Proveedores de puertos](../../../extensibility/debugger/port-suppliers.md)   
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)