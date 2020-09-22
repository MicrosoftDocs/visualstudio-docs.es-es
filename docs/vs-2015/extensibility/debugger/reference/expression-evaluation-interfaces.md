---
title: Interfaces de evaluación de expresiones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8a710019390120768b665cf3b27174831a67f0cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842543"
---
# <a name="expression-evaluation-interfaces"></a>Interfaces de evaluación de expresiones
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 A continuación se muestran las interfaces de evaluación de expresiones para el [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] SDK de depuración.  
  
## <a name="discussion"></a>Debate  
 Estas interfaces se utilizan para evaluar expresiones en una pila de llamadas durante el modo de interrupción. Solo se implementan para los evaluadores de expresiones en tiempo de ejecución de Common Language Runtime (EE).  
  
 Cada interfaz de la tabla muestra el componente que puede implementarlo en la siguiente lista:  
  
- Motor DE depuración (DE)  
  
- Evaluador de expresiones (EE)  
  
- Visual Studio (VS)  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Representa un alias numérico para una variable.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Representa un alias numérico para una variable y permite que un evaluador de expresiones (EE) obtenga el dominio de aplicación para el alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Representa un objeto de matriz.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Representa un objeto de matriz administrado y permite que un evaluador de expresiones (EE) determine el índice base (límites inferiores) de la matriz.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Representa un enlazador que enlaza símbolos de depuración a direcciones reales en la memoria.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Igual que la interfaz [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) , pero proporciona acceso a tipos, alias y visualizadores personalizados.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Representa el evaluador de una expresión.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Representa una versión mejorada de un evaluador de expresiones (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Representa un evaluador de expresiones (EE) con un árbol de analizador mejorado.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Representa una función.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Representa una función y mejora la interfaz [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Permite a un evaluador de expresiones (EE) mostrar un mensaje en la ventana de salida del depurador.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Representa un objeto de código administrado.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interfaz base que representa cualquier símbolo enlazado a una dirección de memoria.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Igual que la interfaz [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , pero proporciona acceso a información adicional.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Representa una expresión analizada lista para su evaluación.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Representa un puntero.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Representa un puntero en un árbol de análisis y extiende la interfaz **IDebugPointerObject** .|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Proporciona la capacidad de modificar el valor de un tipo a través de un visualizador de tipos.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Proporciona acceso a visores personalizados y visualizadores de tipos.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Proporciona la capacidad de crear un objeto [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) .|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Representa una colección de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .|  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Escribir un evaluador de expresiones CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
