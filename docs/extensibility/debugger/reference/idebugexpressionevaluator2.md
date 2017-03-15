---
title: "IDebugExpressionEvaluator2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugExpressionEvaluator2"
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExpressionEvaluator2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa una versión mejorada de un evaluador de expresiones \(EE\).  
  
## Sintaxis  
  
```  
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator  
```  
  
## Notas para los implementadores  
 Esta interfaz se implementa mediante un evaluador de expresiones.  
  
## Métodos  
 Además de los métodos en el [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Recupera un objeto de servicio dado su identificador único.|  
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Carga previamente los módulos designados por el proveedor del símbolo especificado.|  
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Permite que el evaluador de expresiones \(EE\) especificar la interfaz de devolución de llamada que el motor de depurador \(DE\) usará para leer valores de métrica.|  
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Establece la ruta de acceso a common language runtime \(CLR\) cargado en el depurador.|  
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Permite que un motor de depuración pasar una devolución de llamada para el evaluador de expresiones durante la inicialización.|  
|[Terminar](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Detiene y elimina el evaluador de expresiones.|  
  
## Requisitos  
 Encabezado: Ee.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll