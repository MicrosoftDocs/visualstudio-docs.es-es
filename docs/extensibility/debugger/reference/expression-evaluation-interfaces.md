---
title: Interfaces de evaluación de expresiones ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da230a2da87b2dd3e3a85ce3ec6c914e829ccc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736946"
---
# <a name="expression-evaluation-interfaces"></a>Interfaces de evaluación de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 A continuación se muestran las [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaces de evaluación de expresiones para el SDK de depuración.

## <a name="discussion"></a>Discusión
 Estas interfaces se utilizan para evaluar expresiones en una pila de llamadas durante el modo de interrupción. Solo se implementan para evaluadores de expresiones en tiempo de ejecución (EE) de lenguaje común.

 Cada interfaz de la tabla muestra el componente que puede implementarlo de la lista siguiente:

- Motor de depuración (DE)

- Evaluador de expresiones (EE)

- Visual Studio (VS)

|Interfaz|Implementado por|Descripción|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Representa un alias numérico para una variable.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Representa un alias numérico para una variable y permite a un evaluador de expresiones (EE) obtener el dominio de aplicación para el alias.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Representa un objeto de matriz.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Representa un objeto de matriz administrada y permite que un evaluador de expresiones (EE) determine el índice base (límites inferiores) de la matriz.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Representa un enlazador que enlaza símbolos de depuración a direcciones reales en memoria.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Igual que la interfaz [IDebugBinder,](../../../extensibility/debugger/reference/idebugbinder.md) pero proporciona acceso a tipos, alias y visualizadores personalizados.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Representa el evaluador de una expresión.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Representa una versión mejorada de un evaluador de expresiones (EE).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Representa un evaluador de expresiones (EE) con un árbol de analizador mejorado.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Representa una función.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Representa una función y mejora el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz.|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Permite que un evaluador de expresiones (EE) muestre un mensaje en la ventana de salida del depurador.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Representa un objeto de código administrado.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interfaz base que representa cualquier símbolo enlazado a una dirección de memoria.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Igual que el [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interfaz, pero proporciona acceso a información adicional.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Representa una expresión analizada lista para evaluarse.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Representa un puntero.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Representa un puntero en un árbol de análisis y extiende el **IDebugPointerObject** interfaz.|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Proporciona la capacidad de modificar el valor de un tipo a través de un visualizador de tipos.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Proporciona acceso a visores personalizados y visualizadores de tipos.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Proporciona la capacidad de crear un [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objeto.|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Representa una colección de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos.|

## <a name="see-also"></a>Vea también
- [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Escritura de un evaluador de expresiones CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Visualizador de tipo y visor personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
