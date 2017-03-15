---
title: "IDebugDynamicField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDynamicField"
helpviewer_keywords: 
  - "Interfaz IDebugDynamicField"
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDynamicField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

esta interfaz representa un tipo de una variable.  
  
## Sintaxis  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## Notas para los implementadores  
 Esta interfaz se implementa mediante proveedores de símbolos como clase base para cualquier tipo que se puedan determinar en tiempo de ejecución.  Esto es para el código administrado sólo.  
  
## Notas para los llamadores  
 Esta interfaz representa una clase base que especializado más interfaces pueda derivarse.  
  
## métodos en el orden de Vtable  
 Esta interfaz no proporciona ningún método distintos de los heredados de `IDebugField`.  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)