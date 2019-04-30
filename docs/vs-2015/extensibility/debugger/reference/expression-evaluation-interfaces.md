---
title: Interfaces de evaluación de expresión | Microsoft Docs
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435044"
---
# <a name="expression-evaluation-interfaces"></a>Interfaces de evaluación de expresiones
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Los siguientes son las Interfaces de evaluación de expresión para el [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] SDK de depuración.  
  
## <a name="discussion"></a>Discusión  
 Estas interfaces se usan para evaluar expresiones en una pila de llamadas durante el modo de interrupción. Se implementan únicamente para los evaluadores de expresiones en tiempo de ejecución de lenguaje común (EE).  
  
 Cada interfaz de la tabla muestra el componente que se puede implementar en la lista siguiente:  
  
- (DE) del motor de depuración  
  
- Evaluador de expresiones (EE)  
  
- Visual Studio (VS)  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Representa un alias para una variable numérico.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Representa un alias para una variable numérico y permite que un evaluador de expresiones (EE) para obtener el dominio de aplicación para el alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Representa un objeto array.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Representa un objeto de matriz administrada y permite que un evaluador de expresiones (EE) para determinar el índice de base (límites inferiores) de la matriz.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Representa un enlazador que enlaza los símbolos para las direcciones reales en la memoria de depuración.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Igual que el [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfaz, pero proporciona acceso a los tipos, los alias y los visualizadores personalizados.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Representa el evaluador de una expresión.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Representa una versión mejorada de un evaluador de expresiones (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Representa un evaluador de expresiones (EE) con un árbol de analizador mejorada.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Representa una función.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Representa una función y mejora la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Permite que un evaluador de expresiones (EE) mostrar un mensaje en la ventana de salida del depurador.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Representa un objeto de código administrado.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interfaz base que representa cualquier símbolo enlazado a una dirección de memoria.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Igual que el [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz, pero proporciona acceso a información adicional.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Representa una expresión analizada lista para ser evaluada.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Representa un puntero.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Representa un puntero en un árbol de análisis y extiende el **IDebugPointerObject** interfaz.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Proporciona la capacidad de modificar el valor de un tipo a través de un visualizador de tipo.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Proporciona acceso a los visores personalizados y visualizadores de tipo.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Proporciona la capacidad para crear un [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objeto.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Representa una colección de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Escribir un evaluador de expresiones CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
