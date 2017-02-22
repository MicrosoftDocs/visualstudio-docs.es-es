---
title: "IDebugModule2 | Microsoft Docs"
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
  - "IDebugModule2"
helpviewer_keywords: 
  - "Interfaz IDebugModule2"
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugModule2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz representa módulo\-que es, una unidad ejecutable de un programa\-tal como DLL.  
  
## Sintaxis  
  
```  
IDebugModule2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para representar un módulo y para proporcionar acceso a información sobre ese módulo.  
  
## Notas para los llamadores  
 una llamada a [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) devuelve esta interfaz.  El OF envía la interfaz de [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) el administrador de depuración de sesión \(SDM\) mediante el método de [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .  
  
 Esta interfaz también puede devolver en una estructura de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) \(devuelta por una llamada a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)\).  
  
 [Siguiente](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) también devuelve esta interfaz \([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) devuelve la interfaz de [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) \).  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugModule2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|obtiene [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) que describe este módulo.|  
|[ReloadSymbols\_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETO.  NOT UTILICE.  Cargar los símbolos para este módulo.|  
  
## Comentarios  
 La información del módulo se puede mostrar en la ventana de **Módulos** del IDE.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)