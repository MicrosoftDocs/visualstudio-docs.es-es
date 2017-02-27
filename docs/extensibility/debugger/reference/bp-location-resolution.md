---
title: "BP_LOCATION_RESOLUTION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_RESOLUTION"
helpviewer_keywords: 
  - "Estructura BP_LOCATION_RESOLUTION"
ms.assetid: 86ea2c8a-54a3-48e8-83c7-18a515273129
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# BP_LOCATION_RESOLUTION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Describe la resolución de un punto de interrupción en una ubicación concreta.  
  
## Sintaxis  
  
```cpp#  
typedef struct _BP_LOCATION_RESOLUTION {   
   IDebugBreakpointResolution2* pResolution;  
} BP_LOCATION_RESOLUTION;  
```  
  
## Members  
 pResolution  
 El objeto de [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) que determina el tipo de punto de interrupción y su información de resolución.  
  
## Comentarios  
 Esta estructura es miembro de la estructura de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una unión.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)