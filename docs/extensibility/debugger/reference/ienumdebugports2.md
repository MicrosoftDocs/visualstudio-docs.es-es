---
title: "IEnumDebugPorts2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPorts2"
helpviewer_keywords: 
  - "IEnumDebugPorts2"
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPorts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz se enumeran los puertos de un equipo o un proveedor de puerto.  
  
## Sintaxis  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## Notas para los implementadores  
 Un proveedor de puerto implementa esta interfaz para representar una lista de puertos creados por el proveedor.  Visual Studio implementa esta interfaz en compatibilidad con su propio proveedor de puerto.  
  
## Notas para los llamadores  
 Llame a [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) para obtener esta interfaz que representa una lista de puertos creados por el proveedor de puerto.  Llame a [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) para obtener esta interfaz que representa una lista de puertos que se guardaron en el disco.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IEnumDebugPorts2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Recupera un número especificado de puertos en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Omite un número especificado de puertos en una secuencia de enumeración.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Restaura una secuencia de enumeración al principio.|  
|[Clonar](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Crea un enumerador que contiene al mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Obtiene el número de puertos de un enumerador.|  
  
## Comentarios  
 Visual Studio utiliza esta interfaz para ayudar a rellenar una lista de puertos utilizados para asociar los procesos.  
  
 Un motor de depuración no utiliza normalmente esta interfaz.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)