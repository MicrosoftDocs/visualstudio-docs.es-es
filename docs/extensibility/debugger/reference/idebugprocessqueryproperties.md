---
title: "IDebugProcessQueryProperties | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessQueryProperties"
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz es una interfaz de extensión implementada por los implementadores de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) .  Permite al implementador obtener información en el entorno del proceso de depuración.  
  
## Sintaxis  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## Notas para los implementadores  
 Implemente esta interfaz para obtener la información en el entorno de ejecución de un proceso de depuración.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugProcessQueryProperties`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|consultas por un valor de propiedad.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|consultas por valores de propiedad.|  
  
## Comentarios  
 Esta interfaz se implementa en.  
  
## Requisitos  
 encabezado: Portpriv.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)