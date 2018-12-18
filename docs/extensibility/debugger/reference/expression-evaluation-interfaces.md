---
title: Interfaces de evaluación de expresión | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be9582f965fe1d8a00c97548dbc5f458ae4e1198
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107405"
---
# <a name="expression-evaluation-interfaces"></a>Interfaces de evaluación de expresión
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Los siguientes son las Interfaces de evaluación de expresión para el [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK de depuración.  
  
## <a name="discussion"></a>Explicación  
 Estas interfaces se utilizan para evaluar expresiones en una pila de llamadas durante el modo de interrupción. Se implementan solo para los evaluadores de expresiones en tiempo de ejecución de lenguaje común (EE).  
  
 Cada interfaz en la tabla muestra el componente que lo implementan en la lista siguiente:  
  
-   Depurar motor (Alemania)  
  
-   Evaluador de expresiones (EE)  
  
-   Visual Studio (VS)  
  
|Interfaz|Implementado por|Descripción|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Representa un alias para una variable numérico.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Representa un alias para una variable numérico y permite a un evaluador de expresiones (EE) para obtener el dominio de aplicación para el alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Representa un objeto de matriz.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Representa un objeto de matriz administrada y permite que un evaluador de expresiones (EE) para determinar el índice de base (inferior) de la matriz.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Representa un enlazador que enlaza los símbolos para las direcciones reales en la memoria de depuración.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Igual que el [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interfaz pero proporciona acceso a tipos, los alias y los visualizadores personalizados.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Representa el evaluador de una expresión.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Representa una versión mejorada de un evaluador de expresiones (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Representa un evaluador de expresiones (EE) con un árbol de analizador mejorada.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Representa una función.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Representa una función y mejora la [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Permite a un evaluador de expresiones (EE) mostrar un mensaje en la ventana de salida del depurador.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Representa un objeto de código administrado.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interfaz base que representa cualquier símbolo enlazado a una dirección de memoria.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Igual que el [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz pero proporciona acceso a información adicional.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Representa una expresión analizada lista para ser evaluada.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Representa un puntero.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Representa un puntero en un árbol de análisis y amplía la **IDebugPointerObject** interfaz.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Proporciona la capacidad para modificar el valor de un tipo a través de un visualizador de tipo.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Proporciona acceso a los visores personalizados y los visualizadores de tipo.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Proporciona la capacidad para crear un [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objeto.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Representa una colección de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Escribir un evaluador de expresiones de CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)