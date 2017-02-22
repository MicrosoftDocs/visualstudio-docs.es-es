---
title: "Evaluaci&#243;n de expresiones | Microsoft Docs"
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
  - "evaluación de expresiones [SDK de depuración]"
  - "depurar [SDK de depuración], la evaluación de expresiones"
  - "evaluación de expresiones"
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Evaluaci&#243;n de expresiones
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Las expresiones se crean de las cadenas pasadas desde el Automático, reloj, inspección Rápida, o ventanas de Inmediato.  Cuando se evalúa una expresión, genera una cadena imprimible que contiene el nombre y el tipo de variable o argumento y el valor.  Esta cadena se muestra en la ventana correspondiente del IDE.  
  
## Implementación  
 se evalúan las expresiones cuando un programa ha detenido en un punto de interrupción.  La expresión propia se representa mediante una interfaz de [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , que representa una expresión analizada que está lista para enlazar y evalúan dentro del contexto determinado de la evaluación de la expresión.  El marco de pila determina el contexto de la evaluación de la expresión, que proporciona el motor \(DE\) de depuración implementando la interfaz de [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
 Dado un usuario la cadena y una interfaz de [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , un motor de depuración \(DE\) puede obtener una interfaz de [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) pasando la cadena de usuario al método de [IDebugExpressionContext2:: ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) .  la interfaz IDebugExpression2 devuelta contiene la expresión analizada lista para la evaluación.  
  
 Con la interfaz de `IDebugExpression2` , el OF puede obtener el valor de la expresión con la evaluación sincrónica o asincrónica de expresiones, mediante [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  Este valor, junto con el nombre y el tipo de la variable o el argumento, se envía al IDE para la presentación.  El valor, el nombre, y el tipo representan una interfaz de [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
 Para habilitar la evaluación de la expresión, un OF debe implementar las interfaces de [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) y de [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  La evaluación sincrónica y asincrónica requiere la implementación del método de [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .  
  
## Vea también  
 [Marcos de pila](../../extensibility/debugger/stack-frames.md)   
 [Contexto de evaluación de expresión](../../extensibility/debugger/expression-evaluation-context.md)   
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)