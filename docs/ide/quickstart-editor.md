---
title: "Introducción a la edición en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.workload: multiple
ms.openlocfilehash: 614e8856fa8d4c674e40703448399265f2adc456
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-coding-in-the-editor"></a>Inicio rápido: escribir código en el editor

En esta introducción al editor, de 10 minutos de duración, agregaremos código a un archivo para ver algunas de las formas en que Visual Studio hace que escribir y comprender el código (así como recorrerlo) sea más fácil.

## <a name="create-a-new-code-file"></a>Crear un archivo de código

Empezaremos creando un archivo y agregándole código. Cabe mencionar que no hay que crear un proyecto para sacar partido de algunas de las ventajas que el editor ofrece.

1. Abra Visual Studio y, en el menú **Archivo** de la barra de menús, elija **Nuevo** > **Archivo...**

1. En el cuadro de diálogo **Nuevo archivo**, en la categoría **General**, elija **Clase de Visual C#** y, después, elija **Abrir**.

   Se abre un archivo nuevo en el editor con el esqueleto de una clase de C#.

## <a name="using-code-snippets"></a>Uso de fragmentos de código

Visual Studio proporciona fragmentos de código muy prácticos que pueden servir para generar bloques de código de uso común de forma rápida y sencilla. Existen [fragmentos de código](../ide/code-snippets.md) disponibles para diferentes lenguajes de programación, como C#, Visual Basic y C++. Vamos a agregar el fragmento de código de C# `void Main` a nuestro archivo.

1. Coloque el cursor debajo de la llave de cierre del constructor `Class1` y escriba los caracteres `svm`.

   Se abre un cuadro de diálogo de IntelliSense con información sobre el fragmento de código `svm`.

   ![Fragmento de código de IntelliSense](media/quickstart-intellisense-snippet.png)

1. Presione la tecla **TAB** dos veces para insertar el fragmento de código.

   Verá cómo la firma del método `static void Main()` se agrega al archivo. El método `Main()` es el punto de entrada de las aplicaciones de C#.

Los fragmentos de código disponibles varían según el lenguaje. Para ver los fragmentos de código disponibles en el lenguaje de programación que está usando, seleccione **Edición**, **IntelliSense**, **Insertar fragmento de código...** y, seguidamente, elija la carpeta del lenguaje en cuestión. En C#, la lista tiene el siguiente aspecto:

![Lista de fragmentos de código de C#](media/quickstart-code-snippet-list.png)

La lista incluye fragmentos de código para crear (entre otras muchas cosas) una clase, un constructor, `Console.WriteLine()`, bucles `for` o las instrucciones `if` y `switch`.

## <a name="commenting-out-code"></a>Marcar código como comentario

La barra de herramientas proporciona diversos botones con los que será más productivo cuando escriba código. Por ejemplo, puede activar o desactivar el modo de finalización de IntelliSense, aumentar o reducir una sangría, asignar un marcador o marcar código como comentario. En esta sección, marcaremos como comentario parte del código que no queremos compilar.

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
    }

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

1. No vamos a usar la variable `morewords`, pero puede que sí lo hagamos más adelante, así que no la eliminaremos. En su lugar, lo que haremos será convertir esas líneas en comentarios. Seleccione toda la definición de `morewords` hasta el punto y coma final y, luego, seleccione el botón **Marcar como comentario las líneas seleccionadas** en la barra de herramientas o presione **CTRL**+**K**, **CTRL**+**C**.

   ![Botón Marcar como comentario](media/quickstart-comment-out.png)

   Los caracteres de comentario de C# `//` se agregan al principio de cada línea seleccionada para marcar el código como comentario.

## <a name="collapsing-code-blocks"></a>Contraer bloques de código

Queremos que el constructor vacío de `Class1` generado no se vea, así que vamos a contraerlo para tener una vista despejada del código. Seleccione el pequeño cuadro gris con el signo menos que se ve en el margen de la primera línea del constructor. Si prefiere usar el teclado, coloque el cursor en cualquier lugar en el código del constructor y presione **CTRL**+**M**, **CTRL**+**M**.

![Botón para contraer de esquematización](media/quickstart-collapse.png)

El bloque de código se contrae para mostrar únicamente la primera línea seguida de un botón de puntos suspensivos (`...`). Para expandir el bloque de código de nuevo, haga clic en el mismo cuadro gris (que ahora tiene un signo más) o presione **CTRL**+**M**, **CTRL**+**M** otra vez. Esta característica se denomina [esquematización](../ide/outlining.md) y es especialmente útil cuando se contraen métodos muy largos o clases enteras.

## <a name="viewing-symbol-definitions"></a>Ver definiciones de símbolos

Gracias al editor de Visual Studio, es muy sencillo inspeccionar la definición de un tipo, método, etc. Una forma consiste en ir al archivo que contiene la definición, por ejemplo, seleccionando **Ir a definición** en cualquier lugar donde se haga referencia al símbolo. Otra más rápida aún (y que no desplaza el enfoque del archivo en el que está trabajando) es usar [Ver la definición](../ide/go-to-and-peek-definition.md#peek-definition). Vamos a ver la definición de `string`.

1. Haga clic con el botón derecho en cualquier instancia de `string` y seleccione **Ver la definición** en el menú de contenido. También puede presionar **Alt**+**F12**.

   Se abrirá una ventana emergente con la definición de la clase `String`. Puede desplazarse dentro de la ventana emergente o incluso ver la definición de otro tipo desde el código inspeccionado.

   ![Ventana Ver la definición](media/quickstart-peek-definition.png)

1. Para cerrar la ventana de definición inspeccionada, seleccione el pequeño cuadro con una "x" en la esquina superior derecha de la ventana emergente.

## <a name="using-intellisense-to-complete-words"></a>Usar IntelliSense para completar palabras

[IntelliSense](../ide/using-intellisense.md) es un recurso impagable cuando se escribe código. Así, puede mostrar información sobre los miembros disponibles de un tipo o detalles de los parámetros para las distintas sobrecargas de un método. IntelliSense puede servir también para completar una palabra después de escribir una serie de caracteres y, así, eliminar cualquier tipo de ambigüedad. Vamos a agregar una línea de código para imprimir las cadenas ordenadas en la ventana de consola.

1. Empiece a escribir el siguiente código debajo de la variable `query`:

   ```csharp
   foreach (string str in qu
   ```

   Verá cómo IntelliSense muestra **Información rápida** sobre el símbolo `query`.

   ![IntelliSense completa palabras](media/quickstart-intellisense-completion-list.png)

1. Presione la tecla **TAB** para insertar el resto de la palabra `query` por medio de la funcionalidad "Palabra completa" de IntelliSense.

1. Termine el bloque de código de modo que se parezca al siguiente código. Puede incluso practicar usando de nuevo fragmentos de código; para ello, escriba `cw` y, después, presione la tecla **TAB** dos veces para generar el código `Console.WriteLine`.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactoring-a-name"></a>Refactorizar un nombre

Nadie crea código correctamente la primera vez y, en este sentido, una de las cosas que probablemente queramos cambiar es el nombre de una variable o un método. Vamos a probar con la funcionalidad de [refactorización](../ide/refactoring-code-generation-quick-actions.md#refactoring) de Visual Studio para cambiar el nombre de la variable `_words` a `words`.

1. Coloque el cursor sobre la definición de la variable `words`, haga clic con el botón derecho y elija **Cambiar nombre...** en el menú contextual. También puede presionar **CTRL**+**R**, **CTRL**+**R**.

   Se abre un cuadro de diálogo emergente **Cambiar nombre** en la parte superior derecha del editor.

1. Escriba el nombre deseado, `words`. Observe que la referencia a `words` en la consulta también cambia automáticamente de nombre. Antes de presionar **ENTRAR**, active la casilla **Incluir comentarios** del cuadro emergente **Cambiar nombre**.

   ![Cambiar nombre (cuadro de diálogo)](media/quickstart-rename.png)

1. Presione **ENTRAR**.

   Ambas instancias de `words` han cambiado de nombre, así como la referencia a `words` en el comentario de código.

## <a name="next-steps"></a>Pasos siguientes

Ha completado este inicio rápido sobre el editor de Visual Studio. Ahora, quizá le interese probar con otros inicios rápidos sobre el IDE de Visual Studio, hallar otras formas de [desplazarse por el código](../ide/navigating-code.md) o consultar los vínculos abajo indicados para obtener más información sobre las características que hemos visto. En caso contrario, ¡a codificar!

## <a name="see-also"></a>Vea también

[Guía de inicio rápido: Primer vistazo al IDE de Visual Studio](../ide/quickstart-ide-orientation.md)  
[Guía de inicio rápido: Personalizar el IDE de Visual Studio](../ide/quickstart-personalize-the-ide.md)  
[Inicio rápido: proyectos y soluciones](../ide/quickstart-projects-solutions.md)  
[Fragmentos de código](../ide/code-snippets.md)  
[Esquematización](../ide/outlining.md)  
[Ir a definición y Ver la definición](../ide/go-to-and-peek-definition.md)  
[Refactorización](../ide/refactoring-code-generation-quick-actions.md#refactoring)  
[Usar IntelliSense](../ide/using-intellisense.md)  