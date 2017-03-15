---
title: "IDebugExpressionContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionContext2"
helpviewer_keywords: 
  - "Interfaz IDebugExpressionContext2"
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un contexto para la evaluación de expresiones  
  
## Sintaxis  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para representar un contexto en el que una expresión puede evaluar.  
  
## Notas para los llamadores  
 una llamada a [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) devuelve la esta interfaz.  Esta interfaz es accesible cuando se ha pausado el programa que se depura y un marco de pila está disponible.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugExpressionContext2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Recupera el nombre del contexto de evaluación.|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analiza una expresión basada en texto para la evaluación.|  
  
## Comentarios  
 Un contexto de evaluación se puede considerar como el ámbito para realizar la evaluación de la expresión.  
  
 Cuando un programa ha detenido, el administrador de depuración de sesión \(SDM\) obtiene un marco de pila de con una llamada a [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md).  El SDM llama [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obtener la interfaz de `IDebugExpressionContext2` .  Esto va seguida por una llamada a [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para crear una interfaz de [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) , que representa la expresión analizada lista para evaluar.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)