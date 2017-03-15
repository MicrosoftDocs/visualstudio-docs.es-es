---
title: "IDebugFunctionPosition2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionPosition2"
helpviewer_keywords: 
  - "Interfaz IDebugFunctionPosition2"
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa una posición abstracta de una función en un documento de origen.  
  
## Sintaxis  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para representar la posición de una función dentro de un documento de origen.  
  
## Notas para los llamadores  
 Esta interfaz se proporciona como parte de una combinación de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) \(específicamente, una estructura de [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) \) que es a su vez parte de la estructura de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , utilizada en crear un punto de interrupción pendiente.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugFunctionPosition2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Obtiene el nombre de la función que esta posición es relativo.|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|obtiene el desplazamiento desde el principio de la función.|  
  
## Comentarios  
 La posición representada por esta interfaz es basado en texto, específicamente, una estructura de [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)