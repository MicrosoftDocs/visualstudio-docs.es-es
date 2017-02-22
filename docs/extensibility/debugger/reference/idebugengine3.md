---
title: "IDebugEngine3 | Microsoft Docs"
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
  - "IDebugEngine3"
helpviewer_keywords: 
  - "Interfaz IDebugEngine3"
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Representa un único motor \(DE\) de depuración que controla la depuración de uno o más módulos.  
  
## Sintaxis  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## Notas para los implementadores  
 Esta interfaz se implementa mediante una personalizada OF \(si admite símbolos\) para habilitar el estado de JustMyCode.  Esta interfaz se debe implementar al OF si admite símbolos y JustMyCode.  
  
## Notas para los llamadores  
 Esta interfaz es denominada por el administrador de depuración de sesión \(SDM\) para pasar en las opciones de usuario para las ubicaciones de las que cargar símbolos.  También se denomina para establecer el GUID del motor cuando se crean instancias \(este GUID se basa en las métricas desde el registro de motor\).  El SDM también llama a esta interfaz para establecer el estado de JustMyCode y establecer todas las excepciones conocidas por el depurador a un estado especificado.  
  
## métodos en el orden de Vtable  
 Además de los métodos heredados de [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md), la interfaz `IDebugEngine3` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Establece la ruta de acceso o rutas que el OF utilizará para buscar símbolos de depuración.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Carga símbolos para todos los módulos que aún no han tenido sus símbolos cargados.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Informa al De la información de JustMyCode.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Establece el OF GUID de métricas.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Establezca todas las excepciones actualmente excepcionales a un estado especificado.|  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)