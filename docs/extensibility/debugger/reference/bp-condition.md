---
title: "BP_CONDITION | Microsoft Docs"
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
  - "BP_CONDITION"
helpviewer_keywords: 
  - "Estructura BP_CONDITION"
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_CONDITION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Describe las condiciones en las que un punto de interrupción desencadena.  
  
## Sintaxis  
  
```cpp#  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```c#  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## Members  
 `pThread`  
 el objeto de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso activo para la aplicación que contiene el punto de interrupción.  
  
 `styleCondition`  
 Un valor de enumeración de [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) que describe el estilo de esta condición de punto de interrupción.  
  
 `bstrContext`  
 La ubicación del punto de interrupción.  
  
 `bstrCondition`  
 La condición de la esfera de punto de interrupción.  
  
 `nRadix`  
 base que se utilizará en la evaluación de cualquier información numérica.  
  
## Comentarios  
 esta estructura es un miembro de las estructuras de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) y de [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .  
  
 esta estructura también se pasa como parámetro a los métodos de [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) y de [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)