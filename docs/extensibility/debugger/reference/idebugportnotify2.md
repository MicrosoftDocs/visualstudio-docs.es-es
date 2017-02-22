---
title: "IDebugPortNotify2 | Microsoft Docs"
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
  - "IDebugPortNotify2"
helpviewer_keywords: 
  - "Interfaz IDebugPortNotify2"
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz registra o los anula un programa que se puede depurar al puerto que se ejecuta.  
  
## Sintaxis  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## Notas para los implementadores  
 Un proveedor de puerto implementa esta interfaz para admitir la adición y programas el quitar del puerto.  Normalmente se implementa en el mismo objeto que implementa la interfaz de [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) .  
  
## Notas para los llamadores  
 una llamada a [QueryInterface](/visual-cpp/atl/queryinterface) en la interfaz de `IDebugPort2` devuelve esta interfaz.  Además, una llamada a [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) devuelve esta interfaz.  Un motor de depuración puede ver esta interfaz como parámetro a [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugPortNotify2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registra un programa que se puede depurar al puerto que se ejecuta.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Anula que un programa que se puede depurar el puerto se está ejecutando.|  
  
## Comentarios  
 A menos que un puerto de depuración tiene una forma de saber cuándo los programas se cargan o descargados, un proveedor de puerto debe implementar esta interfaz.  Todos los programas que se cargan para depurar a través de un puerto determinado se siguen utilizando esta interfaz.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)