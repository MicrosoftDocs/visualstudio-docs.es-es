---
title: "IDebugPropertyField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyField"
helpviewer_keywords: 
  - "Interfaz IDebugPropertyField"
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPropertyField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz proporciona funciones que permiten la recopilación y el establecimiento de una propiedad.  
  
## Sintaxis  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## Notas para los implementadores  
 Un proveedor de token implementa esta interfaz en el mismo objeto que implementa [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md).  Esta interfaz es una especialización que admite el concepto de propiedades de una clase.  
  
## Notas para los llamadores  
 utilice [QueryInterface](/visual-cpp/atl/queryinterface) para obtener esta interfaz de la interfaz de [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) si el método de [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) devuelve `FIELD_KIND_PROP`.  
  
## métodos en el orden de Vtable  
 Además de los métodos de las interfaces de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) y de [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) , esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|obtiene el método que obtiene la propiedad.|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|obtiene el método que establece la propiedad.|  
  
## Comentarios  
 Una propiedad es un concepto de código administrado y representa un método que se trate como variable.  Las propiedades no existen en C\+\+ no administrado.  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)