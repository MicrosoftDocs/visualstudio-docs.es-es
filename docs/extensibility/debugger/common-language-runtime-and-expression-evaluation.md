---
title: Common Language Runtime y evaluación de expresiones ( Common Language Runtime and Expression Evaluation) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 013579473189dd9310501b76d2de0d5cf6fa5822
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739112"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime y evaluación de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta forma de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte Evaluadores de [expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y Ejemplo de evaluador de [expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Los compiladores, como Visual Basic y C- (pronunciado C-sharp), que se dirigen a Common Language Runtime (CLR), producen Microsoft Intermediate Language (MSIL), que más adelante se compila en código nativo. CLR proporciona un motor de depuración (DE) para depurar el código resultante. Si planea integrar el lenguaje de programación propietario en el IDE de Visual Studio, puede elegir compilar en MSIL y, por lo tanto, no tendrá que escribir su propio DE. Sin embargo, tendrá que escribir un evaluador de expresiones (EE) que sea capaz de evaluar expresiones en el contexto de su lenguaje de programación.

## <a name="discussion"></a>Discusión
 Las expresiones de lenguaje informático generalmente se analizan para generar un conjunto de objetos de datos y un conjunto de operadores utilizados para manipularlos. Por ejemplo, la expresión "A+B" se puede analizar para aplicar el operador de adición (+) a los objetos de datos "A" y "B", lo que puede dar lugar a otro objeto de datos. El conjunto total de objetos de datos, operadores y sus asociaciones se representan con mayor frecuencia en un programa como un árbol, con los operadores en los nodos del árbol y los objetos de datos en las ramas. Una expresión que se ha desglosado en forma de árbol a menudo se denomina árbol analizado.

 Una vez analizada una expresión, se llama a un proveedor de símbolos (SP) para evaluar cada objeto de datos. Por ejemplo, si "A" se define en más de un método, la pregunta "¿Qué A?" debe ser respondido antes de que el valor de A pueda ser determinado. La respuesta devuelta por el SP es algo así como "El tercer elemento en el quinto marco de pila" o "La A que está 50 bytes más allá del inicio de la memoria estática asignada a este método."

 Además de producir MSIL para el propio programa, los compiladores CLR también pueden producir información de depuración muy descriptiva que se escribe en un archivo De base de datos de programa (*.pdb*). Siempre que un compilador de lenguaje propietario genere información de depuración en el mismo formato que los compiladores CLR, el SP de CLR puede identificar los objetos de datos con nombre de ese lenguaje. Una vez que se ha identificado un objeto de datos con nombre, EE utiliza un objeto de enlazador para asociar (o enlazar) el objeto de datos al área de memoria que contiene el valor de ese objeto. A continuación, la DE puede obtener o establecer un nuevo valor para el objeto de datos.

 Un compilador propietario puede proporcionar información de `ISymbolWriter` depuración de CLR llamando a la `System.Diagnostics.SymbolStore`interfaz (que se define en .NET Framework en el espacio de nombres). Al compilar en MSIL y escribir información de depuración a través de estas interfaces, un compilador propietario puede usar CLR DE y SP. Esto simplifica en gran medida la integración de un lenguaje propietario en el IDE de Visual Studio.

 Cuando el CLR DE llama a la EE propietaria para evaluar una expresión, el DE proporciona el EE con interfaces a un SP y un objeto de enlazador. Por lo tanto, escribir un motor de depuración basado en CLR significa que solo es necesario implementar las interfaces de evaluador de expresiones adecuadas; CLR se encarga del enlace y el control de símbolos por usted.

## <a name="see-also"></a>Vea también
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
