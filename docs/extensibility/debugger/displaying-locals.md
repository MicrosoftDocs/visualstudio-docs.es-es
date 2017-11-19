---
title: Mostrar variables locales | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a00d57b8af1c32c2f94334e2930e8f92b166c89b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="displaying-locals"></a>Mostrar variables locales
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ejecución siempre realiza en el contexto de un método, también conocido como el método contenedor o el método actual. Cuando la ejecución se detiene, Visual Studio llama al motor de depuración (Alemania) para obtener una lista de variables locales y argumentos, que se denominan colectivamente las variables locales del método. Visual Studio muestra estas variables locales y sus valores en el **locales** ventana.  
  
 Para mostrar las variables locales, llama a la DE la [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) método perteneciente a la EE y le da un contexto de evaluación, que es, un proveedor de símbolos (SP), la dirección de ejecución actual y un objeto de enlazador. Para obtener más información, consulte [contexto de evaluación](../../extensibility/debugger/evaluation-context.md). Si la llamada se realiza correctamente, el `IDebugExpressionEvaluator::GetMethodProperty` método devuelve un [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto, que representa el método que contiene la dirección de ejecución actual.  
  
 Las llamadas DE [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obtener un [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto, que se filtran para devolver sólo variables locales y enumerar para generar una lista de [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)estructuras. Cada estructura contiene el nombre, tipo y valor de una variable local. El tipo y valor se almacenan como cadenas con formato, adecuadas para su presentación. El nombre, tipo y valor se muestran generalmente juntos en una sola línea de la **locales** ventana.  
  
> [!NOTE]
>  El **Inspección rápida** y **inspección** ventanas también muestran las variables con el mismo formato de nombre, valor y tipo. Sin embargo, esos valores se obtienen mediante una llamada a [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) en lugar de `IDebugProperty2::EnumChildren`.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de ejemplo de variables locales](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Utiliza ejemplos paso a paso a través del proceso de implementación de variables locales.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Contexto de evaluación](../../extensibility/debugger/evaluation-context.md)  
 Explica que, cuando el motor de depuración (Alemania) llama el evaluador de expresiones (EE), pasa tres argumentos.  
  
## <a name="see-also"></a>Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)