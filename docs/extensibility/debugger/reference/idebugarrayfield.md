---
title: "IDebugArrayField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField"
helpviewer_keywords: 
  - "Interfaz IDebugArrayField"
ms.assetid: 9667b0a5-4295-46cc-9388-b75c1350be15
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugArrayField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz describe un símbolo o un tipo de matriz.  
  
## Sintaxis  
  
```  
IDebugArrayField : IDebugContainerField  
```  
  
## Notas para los implementadores  
 El proveedor del token implementa esta interfaz en el mismo objeto que implementa la interfaz de [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) .  Esta interfaz es una especialización que representan objetos de la matriz.  
  
## Notas para los llamadores  
 Utilice [QueryInterface](/visual-cpp/atl/queryinterface) para obtener esta interfaz de la interfaz de [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve el marcador `FIELD_TYPE_ARRAY`.  
  
## métodos en el orden de Vtable  
 Además de los métodos de las interfaces de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) y de [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , esta interfaz implementa lo siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetNumberOfElements](../../../extensibility/debugger/reference/idebugarrayfield-getnumberofelements.md)|Obtiene el número de elementos de la matriz.|  
|[GetElementType](../../../extensibility/debugger/reference/idebugarrayfield-getelementtype.md)|Obtiene el tipo de elemento de la matriz.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayfield-getrank.md)|Obtiene el rango de la matriz.|  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)