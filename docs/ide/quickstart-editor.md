---
title: Introducción a la edición en Visual Studio
ms.date: 11/30/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 93f4dd635e2d90a0ed56b4732c79bb67b569f09b
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511240"
---
# <a name="quickstart-use-the-code-editor"></a>Inicio rápido: uso del editor de código

En esta introducción de 10 minutos al editor de código, se agrega código a un archivo para ver algunas de las formas en que Visual Studio hace que escribir y comprender el código (así como desplazarse por él) sea más fácil.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

En este inicio rápido se presupone que ya está familiarizado con un lenguaje de programación. Si no lo está, le sugerimos que primero lea guías de inicio rápido de programación, como para crear una aplicación web con [Python](../ide/quickstart-python.md) o [C#](../ide/tutorial-csharp-aspnet-core.md), o bien crear una aplicación de consola con [Visual Basic](../ide/quickstart-visual-basic-console.md) o [C++](../ide/getting-started-with-cpp-in-visual-studio.md).

## <a name="create-a-new-code-file"></a>Crear un archivo de código

Empezaremos creando un archivo y agregándole código.

1. Abra Visual Studio y, en el menú **Archivo** de la barra de menús, elija **Nuevo** > **Archivo**.

1. En el cuadro de diálogo **Nuevo archivo**, en la categoría **General**, elija **Clase de Visual C#** y, después, elija **Abrir**.

   Se abre un archivo nuevo en el editor con el esqueleto de una clase de C#. (Observe que no es necesario crear un proyecto de Visual Studio completo para aprovechar algunas de las ventajas que ofrece el editor de código; lo único que se necesita es un archivo de código).

   ![Archivo de código de C# en Visual Studio](media/quickstart-editor.png)

## <a name="use-code-snippets"></a>Uso de fragmentos de código

Visual Studio proporciona *fragmentos de código* muy prácticos que pueden servir para generar bloques de código de uso común de forma rápida y sencilla. Existen [fragmentos de código](../ide/code-snippets.md) disponibles para diferentes lenguajes de programación, como C#, Visual Basic y C++. Vamos a agregar el fragmento de código de C# `void Main` a nuestro archivo.

1. Coloque el cursor justo encima de la llave de cierre final **}** en el archivo y escriba los caracteres `svm` (que es el acrónimo de `static void Main` &mdash;no se preocupe demasiado si no sabe lo que significa).

   Aparece un cuadro de diálogo emergente con información sobre el fragmento de código `svm`.

   ![IntelliSense para fragmento de código en Visual Studio](media/quickstart-intellisense-snippet.png)

1. Presione la tecla **TAB** dos veces para insertar el fragmento de código.

   Verá cómo la firma del método `static void Main()` se agrega al archivo. El método [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) es el punto de entrada de las aplicaciones de C#.

Los fragmentos de código disponibles varían según el lenguaje de programación. Para ver los fragmentos de código disponibles para el lenguaje, seleccione **Editar** > **IntelliSense** > **Insertar fragmento de código** y luego elija la carpeta del lenguaje. En C#, la lista tiene el siguiente aspecto:

![Lista de fragmentos de código de C#](media/quickstart-code-snippet-list.png)

La lista incluye fragmentos de código para crear una [clase](/dotnet/csharp/programming-guide/classes-and-structs/classes), un [constructor](/dotnet/csharp/programming-guide/classes-and-structs/constructors), un bucle [for](/dotnet/csharp/language-reference/keywords/for), una instrucción [if](/dotnet/csharp/language-reference/keywords/if-else) o [switch](/dotnet/csharp/language-reference/keywords/switch), etc.

## <a name="comment-out-code"></a>Marcar código como comentario

La barra de herramientas, que es la fila de botones debajo de la barra de menús de Visual Studio, puede ayudar a mejorar la productividad mientras se codifica. Por ejemplo, puede alternar el modo de finalización de IntelliSense ([IntelliSense](using-intellisense.md) es una ayuda de codificación que muestra una lista de métodos coincidentes, entre otras cosas), aumentar o reducir una sangría de línea o comentar el código que no quiere compilar. En esta sección se comenta algún código.

![Barra de herramientas del editor](media/quickstart-editor-toolbar.png)

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

   ![Botón Marcar como comentario](media/quickstart-comment-out.png)

   Los caracteres de comentario de C# `//` se agregan al principio de cada línea seleccionada para marcar el código como comentario.

## <a name="collapse-code-blocks"></a>Contraer bloques de código

No se quiere ver el [constructor](/dotnet/csharp/programming-guide/classes-and-structs/constructors) vacío de `Class1` generado, así que se contrae para despejar la vista del código. Seleccione el pequeño cuadro gris con el signo menos que se ve en el margen de la primera línea del constructor. Si prefiere usar el teclado, coloque el cursor en cualquier lugar en el código del constructor y presione **Ctrl**+**M**, **Ctrl**+**M**.

![Botón para contraer de esquematización](media/quickstart-collapse.png)

El bloque de código se contrae para mostrar únicamente la primera línea seguida de un botón de puntos suspensivos (`...`). Para expandir el bloque de código de nuevo, haga clic en el mismo cuadro gris (que ahora tiene un signo más) o presione **CTRL**+**M**, **CTRL**+**M** otra vez. Esta característica se denomina [Esquematización](../ide/outlining.md) y es especialmente útil cuando se contraen métodos muy largos o clases enteras.

## <a name="view-symbol-definitions"></a>Ver definiciones de símbolos

Gracias al editor de Visual Studio, es muy sencillo inspeccionar la definición de un tipo, método, etc. Una forma consiste en ir al archivo que contiene la definición, por ejemplo, seleccionando **Ir a definición** en cualquier lugar donde se haga referencia al símbolo. Otra más rápida aún (y que no desplaza el enfoque del archivo en el que está trabajando) es usar [Ver la definición](../ide/go-to-and-peek-definition.md#peek-definition). Vamos a ver la definición del tipo `string`.

1. Haga clic con el botón derecho en cualquier instancia de `string` y elija **Ver la definición** en el menú de contenido. O bien, presione **Alt**+**F12**.

   Se abrirá una ventana emergente con la definición de la clase `String`. Puede desplazarse dentro de la ventana emergente o incluso ver la definición de otro tipo desde el código inspeccionado.

   ![Ventana Ver la definición](media/quickstart-peek-definition.png)

1. Para cerrar la ventana de definición inspeccionada, seleccione el pequeño cuadro con una "x" en la esquina superior derecha de la ventana emergente.

## <a name="use-intellisense-to-complete-words"></a>Usar IntelliSense para completar palabras

[IntelliSense](../ide/using-intellisense.md) es un recurso impagable cuando se escribe código. Así, puede mostrar información sobre los miembros disponibles de un tipo o detalles de los parámetros para las distintas sobrecargas de un método. IntelliSense puede servir también para completar una palabra después de escribir una serie de caracteres y, así, eliminar cualquier tipo de ambigüedad. Se va a agregar una línea de código para imprimir las cadenas ordenadas en la ventana de la consola, que es el lugar estándar para la salida del programa.

1. Empiece a escribir el siguiente código debajo de la variable `query`:

   ```csharp
   foreach (string str in qu
   ```

   Verá cómo IntelliSense muestra **Información rápida** sobre el símbolo `query`.

   ![Finalización de palabras de IntelliSense en Visual Studio](media/quickstart-intellisense-completion-list.png)

1. Presione **Tab** para insertar el resto de la palabra `query` por medio de la funcionalidad de finalización de palabras de IntelliSense.

1. Termine el bloque de código de modo que se parezca al siguiente código. Puede incluso practicar usando de nuevo fragmentos de código; para ello, escriba `cw` y, después, presione la tecla **TAB** dos veces para generar el código `Console.WriteLine`.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refactorizar un nombre

Nadie crea código correctamente la primera vez y una de las cosas que probablemente se tengan que cambiar es el nombre de una variable o un método. Vamos a probar la funcionalidad de [refactorización](../ide/refactoring-in-visual-studio.md) de Visual Studio para cambiar el nombre de la variable `_words` a `words`.

1. Coloque el cursor sobre la definición de la variable `_words`, haga clic con el botón derecho y elija **Cambiar nombre** en el menú contextual, o bien presione **Ctrl**+**R**, **Ctrl**+**R**.

   Se abre un cuadro de diálogo emergente **Cambiar nombre** en la parte superior derecha del editor.

1. Escriba el nombre deseado, **words**. Observe que la referencia a `words` en la consulta también cambia automáticamente de nombre. Antes de presionar **ENTRAR**, active la casilla **Incluir comentarios** del cuadro emergente **Cambiar nombre**.

   ![Cambiar nombre (cuadro de diálogo)](media/quickstart-rename.png)

1. Presione **ENTRAR**.

   Ambas instancias de `words` han cambiado de nombre, así como la referencia a `words` en el comentario de código.

## <a name="next-steps"></a>Pasos siguientes

Ha completado este inicio rápido sobre el editor de Visual Studio. A continuación, podría probar algunos de los otros tutoriales para el entorno de desarrollo de Visual Studio.

> [!div class="nextstepaction"]
> [Guía de inicio rápido: primer vistazo al IDE de Visual Studio](../ide/quickstart-ide-orientation.md)

> [!div class="nextstepaction"]
> [Guía de inicio rápido: personalizar el IDE y el editor de Visual Studio](../ide/quickstart-personalize-the-ide.md)

> [!div class="nextstepaction"]
> [Inicio rápido: proyectos y soluciones](../ide/quickstart-projects-solutions.md)

## <a name="see-also"></a>Vea también

- [Fragmentos de código](../ide/code-snippets.md)
- [Navegación en el código](../ide/navigating-code.md)
- [Esquematización](../ide/outlining.md)
- [Ir a definición y Ver la definición](../ide/go-to-and-peek-definition.md)
- [Refactorización](../ide/refactoring-in-visual-studio.md)
- [Uso de IntelliSense](../ide/using-intellisense.md)
