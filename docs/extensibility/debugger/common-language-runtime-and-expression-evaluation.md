---
title: Common Language Runtime y la evaluación de expresiones | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9e6521f2e38044fc5a333228f5225e42853a42dd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959175"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Evaluación de tiempo de ejecución y la expresión de lenguaje común
> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresión administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Los compiladores, como Visual Basic y C# (pronunciado C-sharp), que tienen como destino Common Language Runtime (CLR), generan Microsoft Intermediate Language (MSIL), que es una versión posterior se compilan en código nativo. CLR proporciona un motor de depuración (DE) para depurar el código resultante. Si va a integrar el lenguaje de programación de propietario en el IDE de Visual Studio, puede elegir compilar en MSIL y, por tanto, no tendrá que escribir su propio DE. Sin embargo, tendrá que escribir un evaluador de expresiones (EE) que es capaz de evaluación de expresiones dentro del contexto de su lenguaje de programación.  
  
## <a name="discussion"></a>Explicación  
 Por lo general se analizan las expresiones de lenguaje del equipo para generar un conjunto de objetos de datos y un conjunto de operadores utilizados para manipularlos. Por ejemplo, la expresión "A + B" es posible que se puede analizar para aplicar el operador de suma (+) a los datos de objetos "A" y "B", lo que puede que otro objeto de datos. El conjunto total de objetos de datos, operadores y sus asociaciones con mayor frecuencia se representan en un programa como un árbol, con los operadores en los nodos del árbol y los objetos de datos en las sucursales. Una expresión que se ha dividido en forma de árbol se suele denominar un árbol analizado.  
  
 Una vez que una expresión que se ha analizado, un proveedor de símbolos (SP) se llama para evaluar cada objeto de datos. Por ejemplo, si "A" se define en más de un método, la pregunta "¿qué un signo?" se deben responder antes de que se puede comprobar el valor de A. La respuesta devuelta por el SP es algo parecido a "El tercer elemento en el marco de pila quinto" o ""la A la que está más allá del principio de la memoria estática de 50 bytes asignado a este método.  
  
 Además de generar MSIL para el propio programa, los compiladores CLR también pueden generar información de depuración muy descriptivo que se escribe en una base de datos de programa (*.pdb*) archivo. Siempre que un compilador del lenguaje de propietario genera información de depuración en el mismo formato que los compiladores CLR, Service Pack de CLR es capaz de identificar que la del lenguaje denominado objetos de datos. Una vez que se ha identificado un objeto de datos con nombre, el EE usa un objeto de enlazador para asociar el objeto de datos (ni enlazarse con él) para el área de memoria que contiene el valor de ese objeto. La DE, a continuación, puede obtener o establecer un nuevo valor para el objeto de datos.  
  
 Un compilador propietario puede proporcionar información de depuración mediante una llamada a CLR el `ISymbolWriter` interfaz (que se define en .NET Framework en el espacio de nombres `System.Diagnostics.SymbolStore`). Si se compila en MSIL y escribir información de depuración a través de estas interfaces, puede usar un compilador propietario el DE CLR y el SP. Esto simplifica en gran medida la integración de un lenguaje propio en el IDE de Visual Studio.  
  
 Cuando la DE CLR llama a la propiedad EE para evaluar una expresión, la DE proporciona el EE con interfaces para un Service Pack y un objeto de enlazador. Por lo tanto, escribir un motor de depuración basados en CLR significa que es necesario solo implementar las interfaces de evaluador de expresión adecuada; el CLR se encarga del enlace y el símbolo por el usuario.  
  
## <a name="see-also"></a>Vea también  
 [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)