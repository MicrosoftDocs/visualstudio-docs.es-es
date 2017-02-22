---
title: "IDebugCodeContext3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugCodeContext3"
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCodeContext3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extiende la interfaz de [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) para habilitar la recuperación del módulo y de interfaces de proceso.  
  
## Sintaxis  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## Notas para los implementadores  
 Implementado por los motores de depuración y usado por el paquete de depuración de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .  
  
## Métodos  
 Además de los métodos de la interfaz de `IDebugCodeContext2` , esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera una referencia a la interfaz del módulo de depuración.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera una referencia a la interfaz del proceso de depuración.|  
  
## Comentarios  
 Ésta es una interfaz opcional que no tiene que normalmente implementar.  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll