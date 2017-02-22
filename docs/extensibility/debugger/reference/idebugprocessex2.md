---
title: "IDebugProcessEx2 | Microsoft Docs"
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
  - "IDebugProcessEx2"
helpviewer_keywords: 
  - "Interfaz IDebugProcessEx2"
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz permite al administrador \(SDM\) de depuración de sesión notificar a un proceso que se está asociando a o se desasociando de proceso.  
  
## Sintaxis  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## Notas para los implementadores  
 Un proveedor de puerto implementa esta interfaz en el mismo objeto que la interfaz de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) para:  
  
-   Admiten el seguimiento de las sesiones conectadas a un proceso  
  
-   Asociación automática admiten a través de los motores varias de depuración  
  
 El proveedor de puerto puede implementar esta interfaz si elige.  
  
## Notas para los llamadores  
  
-   El SDM llama [QueryInterface](/visual-cpp/atl/queryinterface) en una interfaz de `IDebugProcess2` para obtener esta interfaz.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugProcessEx2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa al proceso que una sesión ahora está depurando el proceso.|  
|[Desasociar](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa al proceso que una sesión está depurando no más el proceso.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Agrega los nodos del programa para una lista de los motores de depuración.|  
  
## Comentarios  
 esta interfaz es privada entre el SDM y el proceso.  
  
## Requisitos  
 encabezado: Portpriv.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)