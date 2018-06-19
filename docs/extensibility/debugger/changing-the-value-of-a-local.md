---
title: Cambiar el valor de una variable Local | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 422d1702f319db6da21892bcaa1bd50adad7909d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109590"
---
# <a name="changing-the-value-of-a-local"></a>Cambiar el valor de una variable Local
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando se escribe un nuevo valor en el campo de valor de la **locales** ventana, el paquete de depuración pasa la cadena, como se escribió en el evaluador de expresiones (EE). El EE evalúa esta cadena, que puede contener un valor simple o una expresión y almacena el valor resultante en la variable local asociada.  
  
 Se trata de información general sobre el proceso de cambiar el valor de una variable local:  
  
1.  Cuando el usuario introduce el nuevo valor, Visual Studio llama a [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) en el [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto asociado con el equipo local.  
  
2.  `IDebugProperty2::SetValueAsString` realiza las tareas siguientes:  
  
    1.  Evalúa la cadena para generar un valor.  
  
    2.  Enlaza el asociado [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objeto que se va a obtener un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto.  
  
    3.  Convierte el valor en una serie de bytes.  
  
    4.  Llamadas [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) para colocar los bytes del valor en la memoria para el programa que se está depurando pueda acceder a ellos.  
  
3.  Visual Studio actualiza el **locales** mostrar (vea [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más información).  
  
 Este procedimiento también se utiliza para cambiar el valor de una variable en el **inspección** ventana salvo que es el `IDebugProperty2` objeto asociado con el valor de la variable local que se utiliza en lugar de la `IDebugProperty2` objeto asociado a la variable local sí mismo.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de ejemplo del cambio de valores](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Usa el ejemplo MyCEE paso a paso por el proceso de cambiar los valores.  
  
## <a name="see-also"></a>Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)