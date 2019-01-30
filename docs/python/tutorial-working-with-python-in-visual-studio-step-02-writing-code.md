---
title: Paso 2 del tutorial de Python en Visual Studio, escritura y generación de código
titleSuffix: ''
description: Paso 2 de un tutorial básico sobre las funcionalidades de Python en Visual Studio, entre otras, la edición de código y la ejecución de un proyecto.
ms.date: 01/28/2019
ms.prod: visual-studio-dev15
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6aec7825387c2eda58c76bf885bcd29b0b7bdd1b
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2019
ms.locfileid: "55231784"
---
# <a name="step-2-write-and-run-code"></a>Paso 2: Escritura y ejecución de código

**Paso anterior: [Creación de un proyecto de Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)**

Aunque el **Explorador de soluciones** es donde se administran los archivos del proyecto, la ventana *editor* suele ser donde se trabaja con los *contenidos* de los archivos, como el código fuente. El editor es sensible al contexto del tipo de archivo que está editando, incluido el lenguaje de programación (basado en la extensión del archivo) y ofrece características apropiadas para ese lenguaje, como el color de la sintaxis y la finalización automática de IntelliSense.

1. Después de crear un nuevo proyecto como "Aplicación de Python", se abre un archivo vacío predeterminado *PythonApplication1.py* en el editor de Visual Studio.

1. En el editor, comience a escribir `print("Hello, Visual Studio")` y observe cómo Visual Studio IntelliSense muestra opciones de finalización automática mientras escribe. La opción destacada en la lista desplegable se corresponde con la versión predeterminada que se usaba al presionar la tecla **Tab**. Las finalizaciones son muy útiles cuando se trata de identificadores o instrucciones más largas.

    ![Ventana emergente de finalización automática de IntelliSense](media/vs-getting-started-python-04-IntelliSense1b.png)

1. IntelliSense muestra información diferente en función de la instrucción utilizada, la función invocada, etc. Con la función `print`, al escribir `(` tras `print` para indicar una llamada a la función, se muestra información completa de uso para esa función. La ventana emergente de IntelliSense muestra también el argumento actual en negrita (**value** tal y como se muestra aquí):

    ![Ventana emergente de finalización automática de IntelliSense para una función](media/vs-getting-started-python-05-IntelliSense2b.png)

1. Complete la instrucción para que coincida con lo siguiente:

    ```python
    print("Hello, Visual Studio")
    ```

1. Tenga en cuenta el color de la sintaxis que diferencia la instrucción `print` del argumento `"Hello Visual Studio"`. Además, elimine temporalmente el último `"` de la cadena y observe cómo Visual Studio muestra un subrayado rojo en el código que contiene errores de sintaxis. Luego, vuelva a colocar `"` para corregir el código.

    ![Color de la sintaxis de IntelliSense y resaltado de errores](media/vs-getting-started-python-06-IntelliSense3b.png)

    > [!Tip]
    > Puesto que el entorno de desarrollo de cada uno es muy personal, Visual Studio ofrece un control completo de su apariencia y comportamiento. Seleccione el comando de menú **Herramientas** > **Opciones** y explore los valores de las pestañas **Entorno** y **Editor de texto**. De forma predeterminada, solo se ve un número limitado de opciones. Para ver todas las opciones de todos los lenguajes de programación, seleccione **Mostrar todas las configuraciones** en la parte inferior del cuadro de diálogo.

1. Ejecute el código que ha escrito hasta este punto pulsando **Ctrl**+**F5** o seleccionando el elemento de menú **Depurar** > **Iniciar sin depurar**. Visual Studio le advierte si todavía hay errores en el código.

1. Al ejecutar el programa, aparece una ventana de consola que muestra los resultados, como si ejecutara un intérprete de Python con *PythonApplication1.py* desde la línea de comandos. Presione una tecla para cerrar la ventana y volver al editor de Visual Studio.

    ![Resultado de la primera ejecución del programa](media/vs-getting-started-python-07-output.png)

1. Además de finalizaciones para instrucciones y funciones, IntelliSense ofrece finalizaciones para las instrucciones `import` y `from` de Python. Estas finalizaciones le ayudan a detectar fácilmente qué módulos están disponibles en su entorno y los miembros de esos módulos. En el editor, elimine la línea `print` y comience a escribir `import `. Cuando se escribe el espacio, aparece una lista de módulos:

    ![IntellSense muestra los módulos disponibles para una instrucción import](media/vs-getting-started-python-08-import1.png)

1. Escriba o seleccione `sys` para completar la línea.

1. En la línea siguiente, escriba `from` para volver a ver una lista de módulos:

    ![IntellSense muestra los módulos disponibles para una instrucción from](media/vs-getting-started-python-09-import2.png)

1. Seleccione o escriba `math`, luego agregue un espacio y `import`, para mostrar los miembros del módulo:

    ![IntellSense muestra los miembros del módulo](media/vs-getting-started-python-10-import3.png)

1. Para terminar, importe los miembros `sin`, `cos` y `radians`, con las finalizaciones automáticas disponibles para cada uno de ellos. Cuando haya terminado, el código debería aparecer como sigue:

    ```python
    import sys
    from math import cos, radians
    ```

    > [!Tip]
    > Las finalizaciones se activan con las subcadenas a medida que escribe, mostrando coincidencias con partes de palabras, letras al principio de las palabras e incluso caracteres omitidos. Vea [Edición de código: finalizaciones](editing-python-code-in-visual-studio.md#completions) para obtener información.

1. Agregue un poco más de código para imprimir los valores de coseno de 360 grados:

    ```python
    for i in range(360):
        print(cos(radians(i)))
    ```

1. Vuelva a ejecutar el programa con **Ctrl**+**F5** o **Depurar** > **Iniciar sin depurar**. Cuando haya terminado, cierre la ventana de salida.

## <a name="next-step"></a>Paso siguiente

> [!div class="nextstepaction"]
> [Usar la ventana interactiva de REPL](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="go-deeper"></a>Profundizar un poco más

- [Editar código](editing-python-code-in-visual-studio.md)
- [Código de formato](formatting-python-code.md)
- [Refactorización de código](refactoring-python-code.md)
- [Usar PyLint](linting-python-code.md)
