---
title: "Escribir un evaluador de expresiones de tiempo de ejecución de lenguaje común | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d52a9dbed6cec64426247a0b92bff2b8ec98ec97
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Escribir un evaluador de expresiones de tiempo de ejecución de lenguaje común
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 El evaluador de expresiones (EE) es la parte de un motor de depuración (Alemania) que controla la sintaxis y semántica del lenguaje de programación que generó el código que se está depurando. Expresiones deben evaluarse en el contexto de un lenguaje de programación. Por ejemplo, en algunos idiomas, la expresión "A + B" significa "la suma de A y B." En otros lenguajes, la misma expresión podría significar "A o B." Por lo tanto, otro EE debe estar escrita para cada lenguaje de programación que genera el código de objeto que desea depurar en el IDE de Visual Studio.  
  
 Algunos aspectos del paquete de depuración de Visual Studio deben interpretar el código en el contexto del lenguaje de programación. Por ejemplo, cuando la ejecución se detiene en un punto de interrupción, las expresiones que el usuario ha escrito datos en un **inspección** ventana debe ser evaluada y muestra. Además, el usuario puede cambiar el valor de una variable local, escriba una expresión en una **inspección** ventana o en la **inmediato** ventana.  
  
## <a name="in-this-section"></a>En esta sección  
 [Common Language Runtime y la evaluación de expresiones](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Explica que cuando está integrando el lenguaje de programación propio en el IDE de Visual Studio, escribir un EE capaz de evaluación de expresiones dentro del contexto del lenguaje propietario permite compilar en un lenguaje intermedio de Microsoft (MSIL) sin necesidad de escribir un motor de depuración.  
  
 [Arquitectura del evaluador de expresiones](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Describe cómo implementar las interfaces EE requeridas y llamar al proveedor de símbolos en tiempo de ejecución de common language (SP) y las interfaces de enlazador.  
  
 [Registro de un evaluador de expresiones](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Notas de la EE debe registrarse como un generador de clases con el common language runtime y los entornos de tiempo de ejecución de Visual Studio.  
  
 [Implementación de un evaluador de expresiones](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Describe cómo el proceso de evaluar una expresión incluye el motor de depuración (Alemania), el proveedor de símbolos (SP), el objeto de enlazador y el evaluador de expresiones (EE).  
  
 [Visualización de variables locales](../../extensibility/debugger/displaying-locals.md)  
 Explica cómo, cuando la ejecución se detiene, el paquete de depuración llama a la DE para obtener una lista de las variables locales y argumentos.  
  
 [Evaluación de una expresión de la ventana Inspección](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Documenta cómo el paquete de depuración de Visual Studio llama a la DE para determinar el valor actual de cada expresión en su lista de supervisión.  
  
 [Cambio del valor de una variable local](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Explica que, para cambiar el valor de una variable local, cada línea de la ventana variables locales tiene asociado un objeto que proporciona el nombre, el tipo y el valor actual de una variable local.  
  
 [Implementación de visualizadores de tipo y visores personalizados](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Explica la interfaz que debe ser implementada por los componentes que admiten los visualizadores de tipo y visores personalizados.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)