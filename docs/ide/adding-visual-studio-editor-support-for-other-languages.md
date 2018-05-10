---
title: Agregar compatibilidad con otros lenguajes en el editor de Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: ae9b9dcbed2886344ab8e81932dbd7ad03adfa1f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="adding-visual-studio-editor-support-for-other-languages"></a>Agregar compatibilidad con otros lenguajes en el editor de Visual Studio
Obtenga información sobre la manera en que el editor de Visual Studio admite la lectura y la navegación por los distintos lenguajes de computación y sobre cómo puede agregar compatibilidad con otros lenguajes en el editor de Visual Studio.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Compatibilidad con el uso de colores para la sintaxis, la finalización de instrucciones y Navegar a
 Las características del editor de Visual Studio como el uso de colores para la sintaxis, la finalización de instrucciones y Navegar a pueden ayudarle a leer, crear y editar el código más fácilmente. En la captura de pantalla siguiente se muestra un ejemplo de cómo se edita un script Perl en Visual Studio. Se aplica color automáticamente a la sintaxis. Por ejemplo, los comentarios del código aparecen en color verde, el código en negro, las rutas de acceso en rojo y las instrucciones en azul. El editor de Visual Studio aplica color automáticamente a la sintaxis de todos los lenguajes que admite. Además, cuando se empieza a escribir un objeto o una palabra clave del lenguaje conocidos, la finalización de instrucciones muestra una lista de las posibles instrucciones y objetos. La finalización de instrucciones puede ayudarle a crear código de manera más rápida y fácil.

 ![Colores de sintaxis en script Perl](../ide/media/vside_perledit.png "VSIDE_PerlEdit")

 Visual Studio actualmente ofrece compatibilidad con el uso de colores para la sintaxis y la finalización de instrucciones básicas para los lenguajes siguientes mediante [gramáticas TextMate](https://manual.macromates.com/en/language_grammars). Si su lenguaje favorito no está en la tabla, no se preocupe: puede agregarlo.

|||||||
|-|-|-|-|-|-|
|Bat|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|Ir|JavaDoc|Objective-C|ShaderLab|C#|
|CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|LESS|Plantillas de|SQL|VBNet|
|CSS|INI|LUA|R|Swift|XML|
|Docker|Jade|Make|Ruby|TypeScript|YAML|

 Además del uso de colores para la sintaxis y la finalización de instrucciones básicas, Visual Studio tiene una característica denominada [Navegar a](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Esta característica permite buscar rápidamente archivos de código, rutas de acceso de archivo y símbolos de código. Visual Studio ofrece compatibilidad con Navegar a para los idiomas siguientes.

-   Ir

-   Java

-   JavaScript

-   PHP

-   TypeScript

-   Visual Basic

-   Visual C++

-   C#

Todos estos tipos de archivo tienen las características que se han descrito anteriormente aunque todavía no se haya instalado la compatibilidad con un idioma determinado. La instalación de compatibilidad especializada con algunos lenguajes puede proporcionar compatibilidad con lenguajes adicionales, como IntelliSense u otras características de lenguaje avanzadas, como las bombillas.

## <a name="adding-support-for-non-supported-languages"></a>Agregar compatibilidad con idiomas no admitidos
 Visual Studio 2015 Update 1 y versiones posteriores proporcionan compatibilidad de lenguaje en el editor mediante el uso de [gramáticas TextMate](https://manual.macromates.com/en/language_grammars). Si su lenguaje de programación favorito no se admite actualmente en el editor de Visual Studio, busque en primer lugar en la Web, ya que es posible que exista un lote de TextMate para el lenguaje. Si no encuentra uno, puede agregar usted mismo compatibilidad con él en Visual Studio 2015 Update 1 o versiones posteriores. Para ello, cree un modelo de lote de TextMate para gramáticas del lenguaje y fragmentos de código.

 Agregue todas las gramáticas TextMate nuevas para Visual Studio en la carpeta siguiente:

 *%userprofile%\\.vs\Extensions*

 En esta ruta de acceso base, agregue las carpetas siguientes si se aplican a su situación:

|Nombre de carpeta|Description|
|-----------------|-----------------|
|\\*\<nombre del lenguaje>*|Carpeta del lenguaje. Reemplace *\<nombre del lenguaje>* por el nombre del lenguaje. Por ejemplo, *\Matlab*.|
|*\Syntaxes*|Carpeta de la gramática. Contiene los archivos .*json* de la gramática para el lenguaje, como *Matlab.json*.|
|*\Snippets*|Carpeta de fragmentos de código. Contiene fragmentos de código para el lenguaje.|

 En Windows, *%userprofile%* se resuelve como la ruta de acceso *c:\Usuarios\\\<nombre de usuario>*. Si la carpeta de extensiones no existe en el sistema, debe crearla. Si la carpeta ya existe, estará oculta.

 Para obtener más información sobre cómo crear gramáticas TextMate, vea [TextMate – Introduction to Language Grammars: How to add source code syntax highlighting embedded in HTML](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) (TextMate. Introducción a las gramáticas de lenguaje: cómo agregar resaltado de sintaxis de código origen insertado en HTML) y [Notes on how to create a Language Grammar and Custom Theme for a Textmate Bundle](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle) (Notas sobre cómo crear una gramática de lenguaje y un tema personalizado para un lote de Textmate).

## <a name="see-also"></a>Vea también

- [Mejoras en Navegar a de Visual Studio 2013](https://blogs.msdn.microsoft.com/mvpawardprogram/2013/10/22/visual-studio-2013-navigate-to-improvements/)
- [Tutorial: Crear un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md)
- [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)