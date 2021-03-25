---
title: Common Language Runtime y evaluación de expresiones | Microsoft Docs
description: Obtenga información sobre cómo interactúa Common Language Runtime con el motor de depuración y cómo integrar un lenguaje de programación patentado en el IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 35ddc218d0e9499253269a12687fa89122cfe007
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055016"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime y evaluación de expresiones
> [!IMPORTANT]
> En Visual Studio 2015, esta manera de implementar evaluadores de expresiones está en desuso. Para obtener información sobre la implementación de evaluadores de expresiones CLR, consulte [evaluadores](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) de expresiones CLR y [ejemplo de evaluador de expresiones administradas](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Los compiladores, como Visual Basic y C# (pronunciados con C-Sharp), que tienen como destino Common Language Runtime (CLR), producen el lenguaje intermedio de Microsoft (MSIL), que se compila posteriormente en código nativo. CLR proporciona un motor DE depuración (DE) para depurar el código resultante. Si tiene previsto integrar el lenguaje de programación de su propiedad en el IDE de Visual Studio, puede elegir compilar en MSIL y, por tanto, no tendrá que escribir su propio. Sin embargo, tendrá que escribir un evaluador de expresiones (EE) que sea capaz de evaluar expresiones en el contexto del lenguaje de programación.

## <a name="discussion"></a>Debate
 Normalmente, las expresiones de idioma del equipo se analizan para generar un conjunto de objetos de datos y un conjunto de operadores que se usan para manipularlos. Por ejemplo, la expresión "A + B" podría analizarse para aplicar el operador de suma (+) a los objetos de datos "A" y "B", lo que podría dar lugar a otro objeto de datos. El conjunto total de objetos de datos, operadores y sus asociaciones se representan normalmente en un programa como un árbol, con los operadores en los nodos del árbol y los objetos de datos de las bifurcaciones. Una expresión que se ha dividido en el formato de árbol a menudo se denomina árbol analizado.

 Una vez analizada una expresión, se llama a un proveedor de símbolos (SP) para evaluar cada objeto de datos. Por ejemplo, si "A" se define en más de un método, la pregunta "¿Qué es?" se debe responder antes de que se pueda determinar el valor de un. La respuesta devuelta por el SP es similar a "el tercer elemento del quinto marco de pila" o "el que es 50 bytes más allá del inicio de la memoria estática asignada a este método".

 Además de generar MSIL para el propio programa, los compiladores CLR también pueden generar información de depuración muy descriptiva que se escribe en un archivo de base de datos de programa (*. pdb*). Siempre que un compilador de lenguaje propietario genere información de depuración en el mismo formato que los compiladores de CLR, el SP del CLR podrá identificar los objetos de datos con nombre del lenguaje. Una vez identificado un objeto de datos con nombre, usa un objeto de enlazador para asociar (o enlazar) el objeto de datos al área de memoria que contiene el valor de ese objeto. A continuación, el DE puede obtener o establecer un nuevo valor para el objeto de datos.

 Un compilador propietario puede proporcionar información de depuración de CLR llamando a la `ISymbolWriter` interfaz (que se define en el .NET Framework en el espacio de nombres `System.Diagnostics.SymbolStore` ). Al compilar en MSIL y escribir información de depuración a través de estas interfaces, un compilador propietario puede usar CLR DE y SP. Esto simplifica considerablemente la integración de un lenguaje patentado en el IDE de Visual Studio.

 Cuando el CLR DE llama a la propiedad de EE para evaluar una expresión, el método DE proporciona interfaces de EE a un SP y un objeto de enlazador. Por lo tanto, la escritura de un motor de depuración basado en CLR significa que solo es necesario implementar las interfaces apropiadas del evaluador de expresiones. el CLR se encarga del enlace y el control de los símbolos.

## <a name="see-also"></a>Consulte también
- [Escribir un evaluador de expresiones CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
