---
title: "BP_RESOLUTION_DATA | Microsoft Docs"
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
  - "BP_RESOLUTION_DATA"
helpviewer_keywords: 
  - "Estructura BP_RESOLUTION_DATA"
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_RESOLUTION_DATA
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Describe el resultado de enlazar un punto de interrupción de datos.  
  
## Sintaxis  
  
```cpp#  
typedef struct _BP_RESOLUTION_DATA {   
   BSTR              bstrDataExpr;  
   BSTR              bstrFunc;  
   BSTR              bstrImage;  
   BP_RES_DATA_FLAGS dwFlags;  
} BP_RESOLUTION_DATA;  
```  
  
```c#  
public struct BP_RESOLUTION_DATA {   
   public string bstrDataExpr;  
   public string bstrFunc;  
   public string bstrImage;  
   public uint   dwFlags;  
};  
```  
  
## Members  
 `bstrDataExpr`  
 La expresión de datos se ha enlazado.  
  
 `bstrFunc`  
 El nombre de la función que el punto de interrupción de datos ha enlazado en \(si existe\).  
  
 `bstrImage`  
 El nombre del módulo \(MyModule.dll, por ejemplo\) que el punto de interrupción de datos ha enlazado en.  
  
 `dwFlags`  
 Un valor de enumeración de [BP\_RES\_DATA\_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) , describe cómo se implementa el punto de interrupción de datos.  
  
## Comentarios  
 Esta estructura es miembro de la estructura de [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) , que a su vez un miembro de la estructura de [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) devuelta por el método de [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)