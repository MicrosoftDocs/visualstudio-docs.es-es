---
title: "Common Language Runtime y la evaluaci&#243;n de expresiones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], la evaluación de expresiones"
  - "evaluación de expresiones y common language runtime"
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Common Language Runtime y la evaluaci&#243;n de expresiones
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Compiladores, como Visual Basic y C\# \(pronunciado C sharp\), que tienen como destino Common Language Runtime \(CLR\), generan Microsoft Intermediate Language \(MSIL\), que es una versión posterior se compila a código nativo. CLR proporciona un motor de depuración \(DE\) para depurar el código resultante. Si planea integrar su lenguaje de programación patentado en el IDE de Visual Studio, puede elegir compilar en MSIL y, por tanto, no tendrá que escribir su propio DE. Sin embargo, tendrá que escribir un evaluador de expresiones \(EE\) que es capaz de evaluación de expresiones dentro del contexto de su lenguaje de programación.  
  
## Explicación  
 Expresiones de idioma del equipo generalmente se analizan para generar un conjunto de objetos de datos y un conjunto de operadores utilizados para manipularlos. Por ejemplo, la expresión de que puede analizarse "A \+ B" para aplicar el operador de suma \(\+\) a los datos objetos "A" y "B", resultando posiblemente en otro objeto de datos. El conjunto total de objetos de datos, operadores y sus asociaciones se representan con más frecuencia en un programa como un árbol con los operadores en los nodos del árbol y los objetos de datos en las sucursales. Una expresión que se ha dividido en forma de árbol se suele denominar un árbol analizado.  
  
 Una vez que se ha analizado una expresión, un proveedor de símbolos \(SP\) se llama para evaluar cada objeto de datos. Por ejemplo, si "A" se define en más de un método y, a continuación, la pregunta "¿qué un signo?" se debe responder antes de que se puede comprobar el valor de A. La respuesta devuelta por el SP es algo parecido a "El tercer elemento en el marco de pila quinto" o "El A 50 bytes más allá del principio de la memoria estática asignado a este método."  
  
 Además de generar MSIL para el propio programa, los compiladores CLR también pueden generar información de depuración muy descriptiva que se escribe en un archivo de base de datos de programa \(.pdb\). Siempre que un compilador de lenguaje propietario genera información de depuración en el mismo formato que los compiladores CLR, es capaz de identificar que el nombre del lenguaje de objetos de datos SP de CLR. Una vez identificado un objeto de datos con nombre, EE utiliza un objeto de enlazador para asociar el objeto de datos \(o enlazar\) para el área de memoria que contiene el valor de ese objeto. La DE, a continuación, puede obtener o establecer un nuevo valor para el objeto de datos.  
  
 Un compilador propietario puede proporcionar información de depuración mediante una llamada a CLR el `ISymbolWriter` interfaz \(que se define en .NET Framework en el espacio de nombres `System.Diagnostics.SymbolStore`\). Si se compila en MSIL y escribir información de depuración a través de estas interfaces, puede utilizar un compilador propietario el DE CLR y el SP. Esto simplifica enormemente la integración de un lenguaje patentado en el IDE de Visual Studio.  
  
 Cuando la DE CLR llama a la propiedad EE para evaluar una expresión, la DE suministra EE con interfaces a un SP y un objeto de enlazador. Por lo tanto, escribir un medio de motor de depuración basada en CLR solo es necesario para implementar las interfaces de evaluador de expresión adecuada; el CLR se encarga del enlace y el símbolo por el usuario.  
  
## Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)