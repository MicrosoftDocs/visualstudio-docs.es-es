---
title: 'Tutorial de trabajo con Python, paso 3: la ventana interactiva REPL'
description: Paso 3 de un tutorial básico sobre las funcionalidades de Python en Visual Studio, que trata sobre la ventana interactiva REPL de Python.
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 00a66cb56fb3ada8f48018c644a37189b494cc98
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511761"
---
# <a name="step-3-use-the-interactive-repl-window"></a>Paso 3: Usar la ventana interactiva de REPL

**Paso anterior: [Escribir y ejecutar código](tutorial-working-with-python-in-visual-studio-step-02-writing-code.md)**

La ventana **interactiva** de Visual Studio para Python proporciona una experiencia de lectura-evaluación-impresión-repetición (REPL) que reduce considerablemente el ciclo habitual de edición-compilación-depuración. La ventana **interactiva** proporciona todas las funciones de la experiencia de REPL de la línea de comandos de Python. También resulta muy fácil intercambiar el código con archivos de código fuente en el editor de Visual Studio, que en otros casos es complicado con la línea de comandos.

1. Abra la ventana **interactiva** haciendo clic con el botón derecho en el entorno de Python del proyecto en el **Explorador de soluciones** (por ejemplo, **Python 3.6 (32 bits)** como se muestra en un gráfico anterior) y seleccione **Abrir ventana interactiva**. Como alternativa, puede seleccionar **Ver** > **Otras ventanas** > **Ventanas interactivas de Python** en el menú principal de Visual Studio.

1. Se abre la ventana **interactiva** debajo del editor, con el símbolo estándar del sistema de REPL de Python **>>>**. La lista desplegable **Plataforma** permite seleccionar un intérprete específico con el que trabajar. En muchas ocasiones también querrá aumentar el tamaño de la ventana **interactiva**, lo que puede hacer si arrastra el separador entre las dos ventanas:

    ![Ventana interactiva de Python y arrastre para cambiar el tamaño](media/vs-getting-started-python-11-interactive1b.png)

    > [!Tip]
    > Puede cambiar el tamaño de todas las ventanas en Visual Studio si arrastra los separadores de los bordes. También puede arrastrar las ventanas independientemente del marco de Visual Studio y reorganizarlas como prefiera dentro del marco. Para más información, vea [Personalizar los diseños de ventana](../ide/customizing-window-layouts-in-visual-studio.md).

1. Escriba algunas instrucciones (como `print("Hello, Visual Studio")`) y expresiones (como `123/456`) para ver los resultados inmediatos:

    ![Resultados inmediatos de la ventana interactiva de Python](media/vs-getting-started-python-12-interactive2.png)

1. Al empezar a escribir una instrucción multilínea, como una definición de función, en la ventana **interactiva** se muestra el símbolo **...** de Python para las líneas siguientes que, a diferencia de la línea de comandos de REPL, proporciona sangría automática:

    ![Ventana interactiva de Python con la continuación de la instrucción](media/vs-getting-started-python-13-interactive3.png)

1. La ventana **interactiva** proporciona un historial completo de todo lo que ha escrito y ofrece mejoras con respecto a la línea de comandos de REPL con elementos de historial multilínea. Por ejemplo, puede recuperar fácilmente la definición completa de la función `f` como una única unidad y cambiar el nombre con facilidad a `make_double`, en lugar de tener que volver a crear la función línea por línea.

1. En Visual Studio se pueden enviar varias líneas de código desde una ventana del editor a la ventana **interactiva**. Esta característica permite mantener el código en un archivo de origen y enviar con facilidad elementos seleccionados a la ventana **interactiva**. Después, puede trabajar con estos fragmentos de código en el entorno de REPL rápido en lugar de tener que ejecutar el programa completo. Para ver esta característica, reemplace el bucle `for` del archivo *PythonApplication1.py* por lo siguiente:

    ```python
    # Create a string with spaces proportional to a cosine of x in degrees
    def make_dot_string(x):
        return ' ' * int(20 * cos(radians(x)) + 20) + 'o'
    ```

1. Seleccione solo las instrucciones `import` y `from` del archivo *.py*, haga clic con el botón derecho y seleccione **Enviar a interactivo** (o presione **Ctrl**+**Entrar**). El fragmento de código se pega inmediatamente en la ventana **interactiva** y se ejecuta. Ahora seleccione la función `make_dot_string` y repita el mismo comando, que vuelve a ejecutar este fragmento de código. Dado que el código define una función, puede probarla rápidamente si la invoca varias veces:

    ![Envío y prueba del código en la ventana interactiva](media/vs-getting-started-python-14-interactive4.png)

    > [!Tip]
    > Al presionar **Ctrl**+**Entrar** en el editor *sin* una selección se ejecuta la línea de código actual en la ventana **interactiva** y se coloca automáticamente el símbolo de intercalación en la línea siguiente. Con esta característica, puede presionar varias veces **Ctrl**+**Entrar** para recorrer el código, algo que no era posible hacer solo con la línea de comandos de Python. También permite recorrer el código sin ejecutar el depurador y sin necesidad de iniciar el programa desde el principio.

1. También puede copiar y pegar varias líneas de código en la ventana **interactiva** desde cualquier origen, como el fragmento de código siguiente, lo que es difícil de hacer con el REPL de la línea de comandos de Python. Cuando se pega, la ventana **interactiva** ejecuta el código como si se hubiera escrito:

    ```python
    for i in range(360):
        s = make_dot_string(i)
        print(s)
    ```

    ![Pegar varias líneas de código mediante Enviar a Interactive](media/vs-getting-started-python-15-interactive5.png)

1. Como puede ver, este código funciona correctamente, pero su salida no es muy interesante. Un valor de paso diferente en el bucle `for` mostraría más cantidad de la onda del coseno. Afortunadamente, como todo el bucle `for` aparece en el historial de REPL como una única unidad, se puede volver atrás con facilidad para realizar los cambios que quiera y probar la función de nuevo. Presione la tecla Flecha arriba para recuperar primero el bucle `for`. Después, presione las teclas Flecha izquierda o Flecha derecha para empezar a navegar en el código (hasta que lo haga, las teclas Flecha arriba y Flecha abajo continúan recorriendo el historial). Vaya a la especificación `range` y cámbiela por `range(0, 360, 12)`. Después, presione **Ctrl**+**Entrar** (en cualquier lugar del código) para volver a ejecutar la instrucción completa:

    ![Edición de una instrucción anterior en la ventana interactiva](media/vs-getting-started-python-16-interactive6.png)

1. Repita el proceso para experimentar con valores de paso diferentes hasta que encuentre el que más le guste. También puede hacer que se repita la onda si amplía el intervalo, por ejemplo, `range(0, 1800, 12)`.
 
1. Cuando esté satisfecho con el código escrito en la ventana **interactiva**, selecciónelo, haga clic con el botón derecho, seleccione **Copiar código** (**Ctrl**+**Mayús**+**C**) y péguelo en el editor. Observe que esta característica especial de Visual Studio omite automáticamente cualquier salida y los símbolos `>>>` y `...`. Por ejemplo, en la imagen siguiente se muestra el uso del comando **Copiar código** en una selección que incluye los símbolos y la salida:

    ![Comando Copiar código de la ventana interactiva en una selección con símbolos y salida](media/vs-getting-started-python-17-interactive7.png)

    Al pegar en el editor, solamente se obtiene el código:

    ```python
    for i in range(0, 1800, 12):
        s = make_dot_string(i)
        print(s)
    ```

    Si quiere copiar el contenido exacto de la ventana **interactiva**, incluidos los símbolos y la salida, use el comando **Copiar** estándar.

1. Lo que acaba de hacer es usar el entorno de REPL rápido de la ventana **interactiva** para elaborar los detalles de un pequeño fragmento de código y después lo ha agregado cómodamente al archivo de código fuente del proyecto. Si ahora vuelve a ejecutar el código con **Ctrl**+**F5** (o **Depurar** > **Iniciar sin depurar**), verá los resultados exactos que quería.

## <a name="next-step"></a>Paso siguiente

> [!div class="nextstepaction"]
> [Ejecutar código en el depurador](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)

## <a name="go-deeper"></a>Profundizar un poco más

- [Uso de la ventana interactiva](python-interactive-repl-in-visual-studio.md)
- [Uso de IPython en la ventana interactiva](interactive-repl-ipython.md)
