---
title: Adición de compatibilidad del editor con otros lenguajes
description: Vea cómo el editor de Visual Studio admite la lectura y el desplazamiento por los distintos lenguajes de computación y cómo puede agregar compatibilidad con otros lenguajes.
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5e78f632cdfe3e207e7ce71530d06c2a3b3fc6c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914978"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Agregar compatibilidad con otros lenguajes en el editor de Visual Studio

Obtenga información sobre la manera en que el editor de Visual Studio admite la lectura y la navegación por los distintos lenguajes de computación y sobre cómo puede agregar compatibilidad con otros lenguajes en el editor de Visual Studio.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Compatibilidad con el uso de colores para la sintaxis, la finalización de instrucciones y Navegar a

Las características del editor de Visual Studio como el uso de colores para la sintaxis, la finalización de instrucciones (también conocido como IntelliSense) y _Navegar a_ pueden ayudarle a escribir, crear y editar el código más fácilmente. En la captura de pantalla siguiente se muestra un ejemplo de cómo se edita un script Perl en Visual Studio. Se aplica color automáticamente a la sintaxis. Por ejemplo, los comentarios del código aparecen en color verde, el código en negro, las rutas de acceso en rojo y las instrucciones en azul. El editor de Visual Studio aplica color automáticamente a la sintaxis de todos los lenguajes que admite. Además, cuando se empieza a escribir un objeto o una palabra clave del lenguaje conocidos, la finalización de instrucciones muestra una lista de las posibles instrucciones y objetos. La finalización de instrucciones puede ayudarle a escribir código de manera más rápida y fácil.

![Colores de sintaxis en script Perl](../ide/media/vside_perledit.png)

Visual Studio actualmente ofrece compatibilidad con el uso de colores para la sintaxis y la finalización de instrucciones básicas para los lenguajes siguientes mediante [gramáticas TextMate](https://manual.macromates.com/en/language_grammars). Si su lenguaje favorito no está en la tabla, no se preocupe: puede agregarlo.


- Bat
- F#
- Java
- Markdown
- Rust
- Visual Basic
- Clojure
- Ir
- JavaDoc
- Objective-C
- ShaderLab
- C#
- CMake
- Groovy
- JSON
- Perl
- ShellScript
- Visual C++
- CoffeeScript
- HTML
- LESS
- Python
- SQL
- VBNet
- CSS
- INI
- LUA
- R
- Swift
- XML
- Docker
- Jade
- Make
- Ruby
- TypeScript
- YAML

Además del uso de colores para la sintaxis y la finalización de instrucciones básicas, Visual Studio tiene una característica denominada [Navegar a](/archive/blogs/benwilli/visual-studio-tip-3-use-navigate-to). Esta característica permite buscar rápidamente archivos de código, rutas de acceso de archivo y símbolos de código. Visual Studio ofrece compatibilidad con Navegar a para los idiomas siguientes.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Ir

- Java

- PHP

Todos estos tipos de archivo tienen las características que se han descrito anteriormente, aunque todavía no se haya instalado la compatibilidad con un idioma determinado. La instalación de compatibilidad especializada con algunos lenguajes puede proporcionar compatibilidad con lenguajes adicionales, como IntelliSense u otras características de lenguaje avanzadas, como las bombillas.

## <a name="add-support-for-non-supported-languages"></a>Agregar compatibilidad con idiomas no admitidos

Visual Studio proporciona compatibilidad de lenguaje en el editor mediante [gramáticas TextMate](https://manual.macromates.com/en/language_grammars). Si su lenguaje de programación favorito no se admite actualmente en el editor de Visual Studio, busque en primer lugar en la Web, ya que es posible que exista un lote de TextMate para el lenguaje. Si no encuentra ninguno, puede agregar usted mismo compatibilidad con él mediante la creación de un modelo de lote de TextMate para gramáticas del lenguaje y fragmentos de código.

Agregue todas las gramáticas TextMate nuevas para Visual Studio en la carpeta siguiente:

*%userprofile%\\.vs\Extensions*

En esta ruta de acceso base, agregue las carpetas siguientes si se aplican a su situación:

|Nombre de carpeta|Descripción|
|-----------------|-----------------|
|\\*\<language name>*|Carpeta del lenguaje. Reemplace *\<language name>* por el nombre del lenguaje. Por ejemplo, *\Matlab*.|
|*\Syntaxes*|Carpeta de la gramática. Contiene los archivos .*json* de la gramática para el lenguaje, como *Matlab.json*.|
|*\Snippets*|Carpeta de fragmentos de código. Contiene fragmentos de código para el lenguaje.|

En Windows, *%userprofile%* se resuelve como la ruta de acceso *c:\Usuarios\\\<user name>* . Si la carpeta *Extensiones* no existe en el sistema, debe crearla. Si la carpeta ya existe, estará oculta.

> [!TIP]
> Si tiene cualquier archivo abierto en el editor, debe cerrarlo y volver a abrirlo para ver el resaltado de la sintaxis después de agregar las gramáticas de TextMate.

Para obtener más información sobre cómo crear gramáticas TextMate, vea [TextMate – Introduction to Language Grammars](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) (TextMate. Introducción a las gramáticas de lenguaje) y [Notes on how to create a Language Grammar and Custom Theme for a Textmate Bundle](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle) (Notas sobre cómo crear una gramática de lenguaje y un tema personalizado para un lote de Textmate).

## <a name="see-also"></a>Vea también

- [Agregar una extensión del protocolo de servidor de lenguaje](../extensibility/adding-an-lsp-extension.md)
- [Tutorial: Creación de un fragmento de código](../ide/walkthrough-creating-a-code-snippet.md)
- [Tutorial: Mostrar la finalización de instrucciones](../extensibility/walkthrough-displaying-statement-completion.md)
- [Código de ejemplo: gramática de TextMate](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/TextmateGrammar)
- [Código de ejemplo: compatibilidad con lenguajes personalizados](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/Ook_Language_Integration)