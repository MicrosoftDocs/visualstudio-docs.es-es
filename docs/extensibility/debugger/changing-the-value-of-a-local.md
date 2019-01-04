---
title: Cambiar el valor de una variable Local | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9578ededb468d48c362cdd8defb8e8e548946445
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947197"
---
# <a name="change-the-value-of-a-local"></a>Cambie el valor de una variable local
> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresión administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando se escribe un nuevo valor en el campo de valor de la **variables locales** ventana, el paquete de depuración pasa la cadena, como se escribió en el evaluador de expresiones (EE). EE evalúa esta cadena, que puede contener un valor simple o una expresión y almacena el valor resultante en el equipo local asociado.  
  
 Se trata de información general sobre el proceso de cambiar el valor de una variable local:  
  
1. Cuando el usuario introduce el nuevo valor, Visual Studio llama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) en el [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto asociado con el equipo local.  
  
2. `IDebugProperty2::SetValueAsString` realiza las tareas siguientes:  
  
   1.  Evalúa la cadena para generar un valor.  
  
   2.  Enlaza asociado [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objeto para obtener un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto.  
  
   3.  Convierte el valor en una serie de bytes.  
  
   4.  Las llamadas [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) para colocar los bytes del valor en la memoria para el programa que se está depurando pueda acceder a ellos.  
  
3. Visual Studio actualiza el **variables locales** mostrar (consulte [muestra las variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más información).  
  
   Este procedimiento también se usa para cambiar el valor de una variable en el **inspección** ventana, excepto que está el `IDebugProperty2` objeto asociado con el valor de la variable local que se usa en lugar de la `IDebugProperty2` objeto asociado con el equipo local Sí.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de ejemplo de cambio de valores](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Usa el ejemplo MyCEE paso a paso a través del proceso de cambiar los valores.  
  
## <a name="see-also"></a>Vea también  
 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)