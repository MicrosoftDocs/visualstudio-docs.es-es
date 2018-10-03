---
title: Cambiar el valor de una variable Local | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b24bf833336245ff36384e3f34d83b27ed44a62c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577638"
---
# <a name="changing-the-value-of-a-local"></a>Cambio del valor de una variable local
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [cambiar el valor de una variable Local](https://docs.microsoft.com/visualstudio/extensibility/debugger/changing-the-value-of-a-local).  
  
> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión del evaluador de expresiones Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando se escribe un nuevo valor en el campo de valor de la **variables locales** ventana, el paquete de depuración pasa la cadena, como se escribió en el evaluador de expresiones (EE). EE evalúa esta cadena, que puede contener un valor simple o una expresión y almacena el valor resultante en el equipo local asociado.  
  
 Se trata de información general sobre el proceso de cambiar el valor de una variable local:  
  
1.  Cuando el usuario introduce el nuevo valor, Visual Studio llama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) en el [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto asociado con el equipo local.  
  
2.  `IDebugProperty2::SetValueAsString` realiza las tareas siguientes:  
  
    1.  Evalúa la cadena para generar un valor.  
  
    2.  Enlaza asociado [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objeto para obtener un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto.  
  
    3.  Convierte el valor en una serie de bytes.  
  
    4.  Las llamadas [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) para colocar los bytes del valor en la memoria para el programa que se está depurando pueda acceder a ellos.  
  
3.  Visual Studio actualiza el **variables locales** mostrar (consulte [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más información).  
  
 Este procedimiento también se usa para cambiar el valor de una variable en el **inspección** ventana, excepto porque es el `IDebugProperty2` objeto asociado con el valor de la variable local que se usa en lugar de la `IDebugProperty2` objeto asociado con el equipo local Sí.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de ejemplo del cambio de valores](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Usa el ejemplo MyCEE paso a paso a través del proceso de cambiar los valores.  
  
## <a name="see-also"></a>Vea también  
 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)

