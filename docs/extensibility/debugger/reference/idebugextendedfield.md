---
title: "IDebugExtendedField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugExtendedField"
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugExtendedField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extender los tipos de campos disponibles para admitir genéricos de código administrado.  
  
## Sintaxis  
  
```  
IDebugExtendedField : IDebugField  
```  
  
## Métodos  
 Además de los métodos de la interfaz de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|Recupera la clase extendida de campo especificada.|  
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|determina si el campo representa un tipo cerrado.|  
  
## Requisitos  
 encabezado: Sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll