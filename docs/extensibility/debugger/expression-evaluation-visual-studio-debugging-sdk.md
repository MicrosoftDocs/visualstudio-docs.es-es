---
title: "Evaluaci&#243;n de expresiones (SDK de depuraci&#243;n de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], la evaluación de expresiones"
  - "evaluación de expresiones"
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Evaluaci&#243;n de expresiones (SDK de depuraci&#243;n de Visual Studio)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Durante el modo de interrupción, el IDE debe poder evaluar expresiones simples que implican varias variables de programa.  Para ello, el motor de depuración \(DE\) debe poder analizar y evaluar una expresión que se especifique en una de las ventanas del IDE.  
  
 Las expresiones se crean utilizando el método de [IDebugExpressionContext2:: ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y se representan mediante la interfaz resultante de [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .  
  
 La interfaz de **IDebugExpression2** es implementada por el OF y llama a su método de **EvalAsync** para devolver una interfaz de [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) en el IDE, para mostrar los resultados de la evaluación de expresiones en el IDE.  [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) devuelve una estructura que se puede utilizar para incluir el valor de una expresión en una ventana inspección o en la ventana Variables locales.  
  
 Las llamadas [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) o [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) de administrador de depuración \(SDM\) del paquete o de la sesión de depuración para obtener una interfaz de [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa el resultado de la evaluación.  `IDebugProperty2` tiene métodos que devuelven el nombre, el tipo, y el valor de la expresión.  Esta información se presenta en varias ventanas del depurador.  
  
## Mediante la evaluación de expresiones  
 Para utilizar la evaluación de la expresión, debe implementar el método de [IDebugExpressionContext2:: ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) y todos los métodos de la interfaz de [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , como se muestra en la tabla siguiente.  
  
|Método|Descripción|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Evalúa una expresión de forma asincrónica.|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Finaliza la evaluación asincrónica de la expresión.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Evalúa una expresión de forma sincrónica.|  
  
 La evaluación sincrónica y asincrónica requiere la implementación del método de [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .  la evaluación asincrónica de la expresión requiere la implementación de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## Vea también  
 [Control de ejecución y evaluación de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)