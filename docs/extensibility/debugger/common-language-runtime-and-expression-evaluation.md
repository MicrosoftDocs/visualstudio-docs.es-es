---
title: "Common Language Runtime y la evaluación de expresiones | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba9a9a6b406ad5a94cced7820e6b4581db56eb2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime y la evaluación de expresiones
> [!IMPORTANT]
>  Visual Studio 2015, esta forma de implementar los evaluadores de expresión está en desuso. Para obtener información acerca de cómo implementar los evaluadores de expresión de CLR, vea [evaluadores de expresión de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [Managed expresión evaluador Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Compiladores, como Visual Basic y C# (pronunciado C-sharp), que tienen como destino Common Language Runtime (CLR), generan Microsoft lenguaje intermedio (MSIL), que es una versión posterior se compilan en código nativo. El CLR proporciona un motor de depuración (Alemania) para depurar el código resultante. Si planea integrar su lenguaje de programación propio en el IDE de Visual Studio, puede elegir compilar en MSIL y, por tanto, no tendrá que escribir su propio Alemania. Sin embargo, tendrá que escribir un evaluador de expresiones (EE) que es capaz de la evaluación de expresiones dentro del contexto de su lenguaje de programación.  
  
## <a name="discussion"></a>Explicación  
 Por lo general se analizan las expresiones de lenguaje de equipo para generar un conjunto de objetos de datos y un conjunto de operadores utilizados para manipularlos. Por ejemplo, la expresión "A + B" puede analizarse para aplicar el operador de suma (+) a los datos de objetos "A" y "B", lo cual puede provocar en otro objeto de datos. El conjunto total de objetos de datos, operadores y sus asociaciones con más frecuencia se representan en un programa como un árbol, con los operadores en los nodos del árbol y los objetos de datos en las bifurcaciones. Una expresión que se ha dividido en forma de árbol se suele denominar un árbol analizado.  
  
 Una vez que una expresión que se ha analizado, se llama a un proveedor de símbolos (SP) para evaluar cada objeto de datos. Por ejemplo, si "A" se ha definido en más de un método y, a continuación, la pregunta "¿qué un signo?" debe responder antes de que se puede comprobar el valor de A. La respuesta devuelta por el SP es similar a "El tercer elemento en el marco de pila quinto" o "El A 50 bytes sobrepasa el inicio de la memoria estática se asigna a este método."  
  
 Además de generar MSIL para el propio programa, los compiladores CLR también pueden generar información de depuración muy descriptivo que se escribe en un archivo de base de datos de programa (.pdb). Siempre que un compilador de lenguaje propietario genera información de depuración en el mismo formato que los compiladores CLR, SP de CLR es capaz de identificar que del lenguaje denominado objetos de datos. Una vez que se ha identificado un objeto de datos con nombre, el EE usa un objeto de enlazador para asociar el objeto de datos (o enlazar) hasta el área de memoria que contiene el valor de ese objeto. El Alemania, a continuación, puede obtener o establecer un nuevo valor para el objeto de datos.  
  
 Un compilador propietario puede proporcionar información de depuración mediante una llamada de CLR la `ISymbolWriter` interfaz (que se define en .NET Framework en el espacio de nombres `System.Diagnostics.SymbolStore`). Si se compila en MSIL y escribir información de depuración a través de estas interfaces, puede usar un compilador propietario el CLR Alemania y SP. Esto simplifica considerablemente la integración de un lenguaje propio en el IDE de Visual Studio.  
  
 Cuando la DE CLR llama a la propiedad EE para evaluar una expresión, la DE proporciona el EE con interfaces a un SP y un objeto de enlazador. Por lo tanto, escribir un medio de motor de depuración basado en CLR solo es necesario para implementar las interfaces de evaluador de expresiones adecuado; el CLR se encarga del enlace y el símbolo de por el usuario.  
  
## <a name="see-also"></a>Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)