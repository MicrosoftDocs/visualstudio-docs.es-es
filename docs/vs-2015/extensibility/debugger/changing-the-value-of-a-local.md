---
title: Cambiar el valor de una variable local | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 516725510c5f5bc7baa8bd96d3f7fb969b6589e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842403"
---
# <a name="changing-the-value-of-a-local"></a>Cambio del valor de una variable local
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando se escribe un nuevo valor en el campo de valor de la ventana **variables locales** , el paquete de depuración pasa la cadena como tipo al evaluador de expresiones (EE). La clase EE evalúa esta cadena, que puede contener un valor simple o una expresión, y almacena el valor resultante en la variable local asociada.  
  
 Esta es una introducción al proceso de cambiar el valor de una variable local:  
  
1. Después de que el usuario especifique el nuevo valor, Visual Studio llama a [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) en el objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) asociado a la clase local.  
  
2. `IDebugProperty2::SetValueAsString` realiza las tareas siguientes:  
  
   1. Evalúa la cadena para generar un valor.  
  
   2. Enlaza el objeto [IDebugField](../../extensibility/debugger/reference/idebugfield.md) asociado para obtener un objeto [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) .  
  
   3. Convierte el valor en una serie de bytes.  
  
   4. Llama a [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) para colocar los bytes del valor en la memoria, por lo que el programa que se está depurando puede tener acceso a ellos.  
  
3. Visual Studio actualiza la presentación de **variables locales** (consulte [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más detalles).  
  
   Este procedimiento también se usa para cambiar el valor de una variable en la ventana **inspección** , excepto en que es el `IDebugProperty2` objeto asociado al valor de local que se utiliza en lugar del `IDebugProperty2` objeto asociado al propio local.  
  
## <a name="in-this-section"></a>En esta sección  
 [Implementación de ejemplo de cambio de valores](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Usa el ejemplo MyCEE para recorrer el proceso de cambiar los valores.  
  
## <a name="see-also"></a>Consulte también  
 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)
