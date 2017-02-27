---
title: "BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_FUNC_OFFSET"
helpviewer_keywords: 
  - "Estructura BP_LOCATION_CODE_FUNC_OFFSET"
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_CODE_FUNC_OFFSET
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Describe la ubicación de desplazamiento de un punto de interrupción en una función en código.  
  
## Sintaxis  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {   
   BSTR                     bstrContext;  
   IDebugFunctionPosition2* pFuncPos;  
} BP_LOCATION_CODE_FUNC_OFFSET;  
```  
  
## Members  
 `bstrContext`  
 El contexto de punto de interrupción, normalmente un nombre de método o de función como se explica en una pila de llamadas.  
  
 `pFuncPos`  
 El objeto de [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md) que describe el nombre y la posición relativa desde el principio de la función.  
  
## Comentarios  
 Esta estructura es miembro de la estructura de [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una unión.  
  
 El miembro de `pFuncPos` indica dónde establecer el punto de interrupción de función.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)