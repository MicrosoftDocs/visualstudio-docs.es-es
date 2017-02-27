---
title: "IDebugExpressionEvaluator3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugExpressionEvaluator3"
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa un evaluador de expresiones \(EE\) con un árbol de analizador mejorada.  
  
## Sintaxis  
  
```  
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2  
```  
  
## Notas para los llamadores  
 Esta versión del analizador pasa el proveedor de símbolos y la dirección del marco de la evaluación.  
  
## Métodos  
 Además de los métodos en el [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|Convierte una cadena de expresión en una expresión analizada dada el proveedor de símbolos y la dirección del marco de la evaluación.|  
  
## Requisitos  
 Encabezado: Ee.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll