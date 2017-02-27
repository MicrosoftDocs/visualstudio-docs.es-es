---
title: "Evaluador de expresiones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "expresiones [SDK de depuración]"
  - "depurar [SDK de depuración], la evaluación de expresiones"
  - "evaluación de expresiones"
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Evaluador de expresiones
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los evaluadores de expresión \(EE\) examina la sintaxis de un lenguaje para analizar y evaluar variables y expresiones en tiempo de ejecución, lo que son vistas por el usuario si el IDE está en modo de interrupción.  
  
## Mediante evaluadores de expresión  
 Las expresiones se crean utilizando el método de [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , como sigue:  
  
1.  El motor de depuración \(DE\) implementa la interfaz de [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
2.  El paquete de depuración obtiene un objeto de `IDebugExpressionContext2` de una interfaz de [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) y después llamar al método de `IDebugStackFrame2::ParseText` en él para obtener un objeto de [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .  
  
3.  El paquete de depuración llama al método de [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) o el método de [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obtener el valor de la expresión.  `IDebugExpression2::EvaluateAsync` se denomina de comando y de la ventana Inmediato.  Todos los demás componentes de la interfaz de usuario llama `IDebugExpression2::EvaluateSync`.  
  
4.  El resultado de la evaluación de la expresión es un objeto de [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , que contiene el nombre, el tipo, y el valor de resultado de la evaluación de la expresión.  
  
 Durante la evaluación de la expresión, aa requiere información de componente proveedor de símbolo.  Las fuentes de proveedor de símbolos que información simbólica utilizado para identificar y comprender la expresión analizada.  
  
 Cuando se completa la evaluación asincrónica de expresión, un evento asincrónico es enviado por el OF mediante el administrador \(SDM\) de depuración de la sesión para notificar al IDE que la evaluación de la expresión está completa.  Cuando se completa la evaluación sincrónica de la expresión, el resultado de la evaluación se devuelve de la llamada al método de `IDebugExpression2::EvaluateSync` .  
  
## Notas de implementación  
 Los motores de depuración de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] esperan comunicarse con el evaluador de expresiones mediante interfaces \(CLR\) de Common Language Runtime.  Como resultado, un evaluador de expresiones que ejecuta los motores de depuración de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe admitir CLR \(una lista completa de todo el CLR que las interfaces de depuración se puede encontrar en debugref.doc, que forma parte de [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]\).  
  
## Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)