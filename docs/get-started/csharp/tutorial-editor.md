---
title: Introducción a la edición para desarrolladores de C#
description: En esta introducción al editor de código de Visual Studio de 10 minutos de duración se describen algunas de las formas en que Visual Studio hace que escribir y comprender el código de C# (así como desplazarse por él) sea más fácil.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 72a74c967849703feeb427d89891a023326ca6b7
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234970"
---
# <a name="learn-to-use-the-code-editor-with-c"></a>Información sobre cómo usar el editor de código con C#

En esta introducción de 10 minutos al editor de código en Visual Studio, se agrega código a un archivo para ver algunas de las formas en que Visual Studio hace que escribir y comprender el código de C# (así como desplazarse por él) sea más fácil.

::: moniker range="vs-2017"

> [!TIP]
> Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

::: moniker-end

En este artículo se da por hecho que ya está familiarizado con C#. Si no lo está, le aconsejamos que antes eche un vistazo a un tutorial del tipo [Introducción a C# y ASP.NET Core en Visual Studio](tutorial-aspnet-core.md).

> [!TIP]
> Para realizar los procedimientos de este artículo, asegúrese de que tiene la configuración de C# seleccionada en Visual Studio. Para más información sobre cómo seleccionar configuraciones del entorno de desarrollo integrado (IDE), vea [Select environment settings](visual-studio-ide.md#select-environment-settings) (Seleccionar la configuración del entorno).

## <a name="create-a-new-code-file"></a>Crear un archivo de código

Empezaremos creando un archivo y agregándole código.

::: moniker range="vs-2017"

1. Abra Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Abra Visual Studio. Presione **Esc** o haga clic en **Continuar sin código** en la ventana de inicio para abrir el entorno de desarrollo.

::: moniker-end

2. En el menú **Archivo** de la barra de menús, elija **Nuevo** > **Archivo** o presione **Ctrl**+**N**.

3. En el cuadro de diálogo **Nuevo archivo**, en la categoría **General**, elija **Clase de Visual C#** y, después, elija **Abrir**.

   Se abre un archivo nuevo en el editor con el esqueleto de una clase de C#. (Observe que no es necesario crear un proyecto de Visual Studio completo para aprovechar algunas de las ventajas que ofrece el editor de código; lo único que se necesita es un archivo de código).

   ![Archivo de código de C# en Visual Studio](../media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Uso de fragmentos de código

Visual Studio proporciona *fragmentos de código* muy prácticos que pueden servir para generar bloques de código de uso común de forma rápida y sencilla. Existen [fragmentos de código](../../ide/code-snippets.md) disponibles para diferentes lenguajes de programación, como C#, Visual Basic y C++. Vamos a agregar el fragmento de código de C# `void Main` a nuestro archivo.

1. Coloque el cursor justo encima de la llave de cierre final **}** en el archivo y escriba los caracteres `svm` (que es el acrónimo de `static void Main`&mdash;no se preocupe demasiado si no sabe lo que significa).

   Aparece un cuadro de diálogo emergente con información sobre el fragmento de código `svm`.

   ![IntelliSense para fragmento de código en Visual Studio](../media/tutorial-intellisense-snippet.png)

1. Presione la tecla **TAB** dos veces para insertar el fragmento de código.

   Verá cómo la firma del método `static void Main()` se agrega al archivo. El método [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) es el punto de entrada de las aplicaciones de C#.

Los fragmentos de código disponibles varían según el lenguaje de programación. Para ver los fragmentos de código disponibles para el lenguaje, seleccione **Editar** > **IntelliSense** > **Insertar fragmento de código** o presione **Ctrl**+**K**, **Ctrl**+**X** y, después, elija la carpeta del lenguaje. En C#, la lista tiene el siguiente aspecto:

![Lista de fragmentos de código de C#](../media/tutorial-code-snippet-list.png)

La lista incluye fragmentos de código para crear una [clase](/dotnet/csharp/programming-guide/classes-and-structs/classes), un [constructor](/dotnet/csharp/programming-guide/classes-and-structs/constructors), un bucle [for](/dotnet/csharp/language-reference/keywords/for), una instrucción [if](/dotnet/csharp/language-reference/keywords/if-else) o [switch](/dotnet/csharp/language-reference/keywords/switch), etc.

## <a name="comment-out-code"></a>Marcar código como comentario

La barra de herramientas, que es la fila de botones debajo de la barra de menús de Visual Studio, puede ayudar a mejorar la productividad mientras se codifica. Por ejemplo, puede alternar el modo de finalización de IntelliSense ([IntelliSense](../../ide/using-intellisense.md) es una ayuda de codificación que muestra una lista de métodos coincidentes, entre otras cosas), aumentar o reducir una sangría de línea o comentar el código que no quiere compilar. En esta sección se comenta algún código.

![Barra de herramientas del editor](../media/tutorial-editor-toolbar.png)

1. Pegue el siguiente código en el cuerpo del método `Main()`.

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    };

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. No se usa la variable `morewords`, pero puede que sí se haga más adelante, así que no se elimina por completo. En su lugar, lo que haremos será convertir esas líneas en comentarios. Seleccione toda la definición de `morewords` hasta el punto y coma final, y luego haga clic en el botón **Marcar como comentario las líneas seleccionadas** en la barra de herramientas. Si prefiere usar el teclado, presione **Ctrl**+**K**, **Ctrl**+**C**.

   ![Botón Marcar como comentario](../media/tutorial-comment-out.png)

   Los caracteres de comentario de C# `//` se agregan al principio de cada línea seleccionada para marcar el código como comentario.

## <a name="collapse-code-blocks"></a>Contraer bloques de código

No se quiere ver el [constructor](/dotnet/csharp/programming-guide/classes-and-structs/constructors) vacío de `Class1` generado, así que se contrae para despejar la vista del código. Seleccione el pequeño cuadro gris con el signo menos que se ve en el margen de la primera línea del constructor. Si prefiere usar el teclado, coloque el cursor en cualquier lugar en el código del constructor y presione **Ctrl**+**M**, **Ctrl**+**M**.

![Botón para contraer de esquematización](../media/tutorial-collapse.png)

El bloque de código se contrae para mostrar únicamente la primera línea seguida de un botón de puntos suspensivos (`...`). Para expandir el bloque de código de nuevo, haga clic en el mismo cuadro gris (que ahora tiene un signo más) o presione **CTRL**+**M**, **CTRL**+**M** otra vez. Esta característica se denomina [Esquematización](../../ide/outlining.md) y es especialmente útil cuando se contraen métodos muy largos o clases enteras.

## <a name="view-symbol-definitions"></a>Ver definiciones de símbolos

Gracias al editor de Visual Studio, es muy sencillo inspeccionar la definición de un tipo, método, etc. Una forma consiste en ir al archivo que contiene la definición, por ejemplo, seleccionando **Ir a definición** o presionando **F12** en cualquier lugar donde se haga referencia al símbolo. Otra más rápida aún (y que no desplaza el enfoque del archivo en el que está trabajando) es usar [Ver la definición](../../ide/go-to-and-peek-definition.md#peek-definition). Vamos a ver la definición del tipo `string`.

1. Haga clic con el botón derecho en cualquier instancia de `string` y elija **Ver la definición** en el menú de contenido. O bien, presione **Alt**+**F12**.

   Se abrirá una ventana emergente con la definición de la clase `String`. Puede desplazarse dentro de la ventana emergente o incluso ver la definición de otro tipo desde el código inspeccionado.

   ![Ventana Ver la definición](../media/tutorial-peek-definition.png)

1. Para cerrar la ventana de definición inspeccionada, seleccione el pequeño cuadro con una "x" en la esquina superior derecha de la ventana emergente.

## <a name="use-intellisense-to-complete-words"></a>Usar IntelliSense para completar palabras

[IntelliSense](../../ide/using-intellisense.md) es un recurso impagable cuando se escribe código. Así, puede mostrar información sobre los miembros disponibles de un tipo o detalles de los parámetros para las distintas sobrecargas de un método. IntelliSense puede servir también para completar una palabra después de escribir una serie de caracteres y, así, eliminar cualquier tipo de ambigüedad. Se va a agregar una línea de código para imprimir las cadenas ordenadas en la ventana de la consola, que es el lugar estándar para la salida del programa.

1. Empiece a escribir el siguiente código debajo de la variable `query`:

   ```csharp
   foreach (string str in qu
   ```

   Verá cómo IntelliSense muestra **Información rápida** sobre el símbolo `query`.

   ![Finalización de palabras de IntelliSense en Visual Studio](../media/tutorial-intellisense-completion-list.png)

1. Presione **Tab** para insertar el resto de la palabra `query` por medio de la funcionalidad de finalización de palabras de IntelliSense.

1. Termine el bloque de código de modo que se parezca al siguiente código. Puede incluso practicar usando de nuevo fragmentos de código; para ello, escriba `cw` y, después, presione la tecla **TAB** dos veces para generar el código `Console.WriteLine`.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refactorizar un nombre

Nadie crea código correctamente la primera vez y una de las cosas que probablemente se tengan que cambiar es el nombre de una variable o un método. Vamos a probar la funcionalidad de [refactorización](../../ide/refactoring-in-visual-studio.md) de Visual Studio para cambiar el nombre de la variable `_words` a `words`.

1. Coloque el cursor sobre la definición de la variable `_words`, haga clic con el botón derecho y elija **Cambiar nombre** en el menú contextual, o bien presione **Ctrl**+**R**, **Ctrl**+**R**.

   Se abre un cuadro de diálogo emergente **Cambiar nombre** en la parte superior derecha del editor.

1. Escriba el nombre deseado, **words**. Observe que la referencia a `words` en la consulta también cambia automáticamente de nombre. Antes de presionar **ENTRAR**, active la casilla **Incluir comentarios** del cuadro emergente **Cambiar nombre**.

   ![Cambiar nombre (cuadro de diálogo)](../media/tutorial-rename.png)

1. Presione **ENTRAR**.

   Ambas instancias de `words` han cambiado de nombre, así como la referencia a `words` en el comentario de código.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Información sobre proyectos y soluciones](../tutorial-projects-solutions.md)

## <a name="see-also"></a>Vea también

- [Fragmentos de código](../../ide/code-snippets.md)
- [Navegación en el código](../../ide/navigating-code.md)
- [Esquematización](../../ide/outlining.md)
- [Ir a definición y Ver la definición](../../ide/go-to-and-peek-definition.md)
- [Refactorización](../../ide/refactoring-in-visual-studio.md)
- [Uso de IntelliSense](../../ide/using-intellisense.md)
