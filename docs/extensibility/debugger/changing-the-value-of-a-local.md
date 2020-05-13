---
title: Cambio del valor de un local ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98e40e4b6ea10bb6ff1242f23f1b6dd83ce0c0cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739138"
---
# <a name="change-the-value-of-a-local"></a>Cambiar el valor de un local
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Cuando se escribe un nuevo valor en el campo de valor de la ventana **Locales,** el paquete de depuración pasa la cadena, tal como está escrita, al evaluador de expresiones (EE). El EE evalúa esta cadena, que puede contener un valor simple o una expresión, y almacena el valor resultante en el local asociado.

 Esta es una visión general del proceso de cambio del valor de un local:

1. Después de que el usuario escribe el nuevo valor, Visual Studio llama a [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) en el [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto asociado a la local.

2. `IDebugProperty2::SetValueAsString` realiza las siguientes tareas:

   1. Evalúa la cadena para generar un valor.

   2. Enlaza el objeto [IDebugField](../../extensibility/debugger/reference/idebugfield.md) asociado para obtener un objeto [IDebugObject.](../../extensibility/debugger/reference/idebugobject.md)

   3. Convierte el valor en una serie de bytes.

   4. Llama a [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) para colocar los bytes del valor en la memoria para que el programa que se está depurando pueda tener acceso a ellos.

3. Visual Studio actualiza la presentación **Locales** (consulte [Mostrar configuraciones regionales](../../extensibility/debugger/displaying-locals.md) para obtener más información).

   Este procedimiento también se utiliza para cambiar el valor de una variable en la ventana **Inspección,** excepto que es el `IDebugProperty2` objeto asociado con el valor del local que se utiliza en lugar del `IDebugProperty2` objeto asociado al propio local.

## <a name="in-this-section"></a>En esta sección
 [Ejemplo de implementación de valores cambiantes](../../extensibility/debugger/sample-implementation-of-changing-values.md) Utiliza el ejemplo MyCEE para recorrer paso a paso el proceso de cambio de valores.

## <a name="see-also"></a>Vea también
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Mostrando locales](../../extensibility/debugger/displaying-locals.md)
