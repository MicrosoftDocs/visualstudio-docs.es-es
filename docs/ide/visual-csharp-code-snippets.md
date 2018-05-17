---
title: Fragmentos de código de C#
ms.date: 06/05/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b9d494b1fb6465c1cf246f6becb9b812115e6076
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="c-code-snippets"></a>Fragmentos de código de C#

Los fragmentos de código están listos para usar y puede insertarlos rápidamente en el código. Por ejemplo, el fragmento de código `for` crea un bucle `for` vacío. Algunos fragmentos de código son envolventes, lo que permite seleccionar líneas de código y después elegir un fragmento de código que incorpore las líneas de código seleccionadas. Por ejemplo, al seleccionar líneas de código y activar después el fragmento de código `for`, se creará un bucle `for` que incluirá dichas líneas en su bloque. De este modo, los fragmentos de código hacen de la escritura de código de programación un proceso más rápido, sencillo y fiable.

 Puede insertar un fragmento de código en la posición del cursor o insertar un fragmento de código envolvente alrededor del código seleccionado actualmente. La herramienta de inserción de fragmento de código se invoca a través de los comandos **Insertar fragmento de código** o **Envolver con** del menú **IntelliSense**, o con los métodos abreviados de teclado **Ctrl**+**K**, **X** o **Ctrl**+**K**, **S** respectivamente.

 La herramienta de **inserción de fragmento de código** muestra el nombre de todos los fragmentos de código disponibles. La herramienta de inserción de fragmento de código también incluye un cuadro de diálogo de entrada en el que puede escribir el nombre del fragmento de código o parte de este. La herramienta de inserción de fragmento de código resalta la coincidencia más cercana a un nombre de fragmento de código. Si se presiona **TAB** en cualquier momento, se cerrará la herramienta de inserción de fragmento de código y se insertará el fragmento de código seleccionado actualmente. Si se presiona **ESC** o se hace clic con el mouse en el editor de código, se cerrará la herramienta de inserción de fragmento de código sin insertar ningún fragmento de código.

## <a name="default-code-snippets"></a>Fragmentos de código predeterminados

Los siguientes fragmentos de código se incluyen en Visual Studio para C# de manera predeterminada.

|Nombre (o acceso directo)|Description|Ubicaciones válidas donde se puede insertar el fragmento|
|--------------------------|-----------------|---------------------------------------|
|#if|Crea una directiva [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) y una directiva [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif).|En cualquier lugar.|
|#region|Crea una directiva [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) y una directiva [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion).|En cualquier lugar.|
|~|Crea un destructor [finalizador](/dotnet/csharp/programming-guide/classes-and-structs/destructors) para la clase contenedora.|Dentro de una clase.|
|Atributo|Crea una declaración para una clase que se deriva de <xref:System.Attribute>.|Dentro de un espacio de nombres (incluido el espacio de nombres global), una clase o un struct.|
|checked|Crea un bloque [checked](/dotnet/csharp/language-reference/keywords/checked).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|clase|Crea una declaración de clase.|Dentro de un espacio de nombres (incluido el espacio de nombres global), una clase o un struct.|
|ctor|Crea un constructor para la clase contenedora.|Dentro de una clase.|
|cw|Crea una llamada a <xref:System.Console.WriteLine%2A>.|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|do|Crea un bucle [do](/dotnet/csharp/language-reference/keywords/do)`while`.|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|else|Crea un bloque [else](/dotnet/csharp/language-reference/keywords/if-else).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|enum|Crea una declaración [enum](/dotnet/csharp/language-reference/keywords/enum).|Dentro de un espacio de nombres (incluido el espacio de nombres global), una clase o un struct.|
|equals|Crea una declaración de método que invalida el método <xref:System.Object.Equals%2A> que se define en la clase <xref:System.Object>.|Dentro de una clase o un struct.|
|exception|Crea una declaración de una clase que deriva de una excepción (<xref:System.Exception> de manera predeterminada).|Dentro de un espacio de nombres (incluido el espacio de nombres global), una clase o un struct.|
|for|Crea un bucle [for](/dotnet/csharp/language-reference/keywords/for).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|foreach|Crea un bucle [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|forr|Crea un bucle [for](/dotnet/csharp/language-reference/keywords/for) que disminuye la variable de bucle después de cada iteración.|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|if|Crea un bloque [if](/dotnet/csharp/language-reference/keywords/if-else).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|indizador|Crea una declaración de indexador.|Dentro de una clase o un struct.|
|interfaz|Crea una declaración [interface](/dotnet/csharp/language-reference/keywords/interface).|Dentro de un espacio de nombres (incluido el espacio de nombres global), una clase o un struct.|
|invoke|Crea un bloque que invoca un evento de manera segura.|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|iterator|Crea un iterador.|Dentro de una clase o un struct.|
|iterindex|Crea un par de iterador e indexador "con nombre" mediante una clase anidada.|Dentro de una clase o un struct.|
|bloquear|Crea un bloque [lock](/dotnet/csharp/language-reference/keywords/lock-statement).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|mbox|Crea una llamada a <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Puede que tenga que agregar una referencia a *System.Windows.Forms.dll*.|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|namespace|Crea una declaración [namespace](/dotnet/csharp/language-reference/keywords/namespace).|Dentro de un espacio de nombres (incluido el espacio de nombres global).|
|prop|Crea una declaración de [propiedad autoimplementada](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).|Dentro de una clase o un struct.|
|propfull|Crea una declaración de propiedad con descriptores de acceso `get` y `set`.|Dentro de una clase o un struct.|
|propg|Crea una [propiedad autoimplementada](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) de solo lectura con un descriptor de acceso `set` privado.|Dentro de una clase o un struct.|
|sim|Crea una declaración de método Main [static](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int).|Dentro de una clase o un struct.|
|struct|Crea una declaración [struct](/dotnet/csharp/language-reference/keywords/struct).|Dentro de un espacio de nombres (incluido el espacio de nombres global), una clase o un struct.|
|svm|Crea una declaración de método Main [static](/dotnet/csharp/language-reference/keywords/static) [void](/dotnet/csharp/language-reference/keywords/void).|Dentro de una clase o un struct.|
|switch|Crea un bloque [switch](/dotnet/csharp/language-reference/keywords/switch).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|try|Crea un bloque [try-catch](/dotnet/csharp/language-reference/keywords/try-catch).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|tryf|Crea un bloque [try-finally](/dotnet/csharp/language-reference/keywords/try-finally).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|unchecked|Crea un bloque [unchecked](/dotnet/csharp/language-reference/keywords/unchecked).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|unsafe|Crea un bloque [unsafe](/dotnet/csharp/language-reference/keywords/unsafe).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|
|utilizar|Crea una directiva [using](/dotnet/csharp/language-reference/keywords/using-directive).|Dentro de un espacio de nombres (incluido el espacio de nombres global).|
|while|Crea un bucle [while](/dotnet/csharp/language-reference/keywords/while).|Dentro de un método, un indexador, un descriptor de acceso a propiedad o un descriptor de acceso a evento.|

## <a name="see-also"></a>Vea también

- [Funciones de los fragmentos de código](../ide/code-snippet-functions.md)
- [Fragmentos de código](../ide/code-snippets.md)
- [Parámetros de plantilla](../ide/template-parameters.md)
- [Cómo usar fragmentos de código envolventes](../ide/how-to-use-surround-with-code-snippets.md)