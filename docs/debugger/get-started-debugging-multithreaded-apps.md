---
title: Obtenga información sobre cómo depurar aplicaciones multiproceso
description: Depurar con las ventanas Inspección paralela y pilas paralelas en Visual Studio
ms.custom: ''
ms.date: 11/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5535228f8e070128cfa2479d8017d3a88dc0915c
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790256"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Empezar a depurar aplicaciones multiproceso (C#, Visual Basic, C++)

Visual Studio proporciona varias herramientas y elementos de interfaz de usuario para ayudar a depurar aplicaciones multiproceso. Este tutorial muestra cómo usar los marcadores de subprocesos, el **pilas paralelas** ventana, el **inspección paralela** ventana puntos de interrupción condicionales y los puntos de interrupción de filtro. Completar este tutorial le permitirá familiarizarse con las características de Visual Studio para depurar aplicaciones multiproceso.

Estos dos temas proporcionan información adicional sobre el uso de otras herramientas de depuración multiproceso:

- Para usar el **ubicación de depuración** barra de herramientas y la **subprocesos** ventana, consulte [Tutorial: depurar una aplicación multiproceso](../debugger/how-to-use-the-threads-window.md).

- Para obtener un ejemplo que usa <xref:System.Threading.Tasks.Task> (código administrado) y el runtime de simultaneidad (C++), consulte [Tutorial: Depuración de una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md). Para sugerencias de depuración generales que se aplican a los tipos de aplicaciones multiproceso más, lea ese tema y ésta.

En primer lugar, necesitará un proyecto de aplicación multiproceso. A continuación se muestra un ejemplo.

## <a name="create-a-multithreaded-app-project"></a>Crear un proyecto de aplicación multiproceso

1. Abra Visual Studio y cree un nuevo proyecto.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Tipo **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **consola** (o **c ++**), elija **plantillas**y, a continuación:

    - Para C# o Visual Basic, elija **crear nuevo proyecto de aplicación de consola (.NET Framework)** cualquiera C# o Visual Basic. En el cuadro de diálogo que se abre, elija **Crear**.
    - Para C++, elija **crear nuevo proyecto de aplicación de consola** para C++. En el cuadro de diálogo que se abre, elija **Crear**.

    A continuación, escriba un nombre como **MyThreadWalkthroughApp** y haga clic en **crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, seleccione lo siguiente:

    - Para un C# aplicación, en **Visual C#** , elija **Windows Desktop**y, a continuación, en el panel central, elija **aplicación de consola (.NET Framework)**.
    - Para una aplicación de Visual Basic, en **Visual Basic**, elija **Windows Desktop**y, a continuación, en el panel central, elija **aplicación de consola (.NET Framework)**.
    - Para una aplicación de C++, en **Visual C++**, elija **Windows Desktop**,, y, a continuación, elija **aplicación de consola Windows**.

    A continuación, escriba un nombre como **MyThreadWalkthroughApp** y haga clic en **Aceptar**.
    ::: moniker-end

    Si no ve la plantilla de proyecto **Aplicación de consola**, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo de escritorio de .NET** o **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

1. Seleccione **Aceptar**.

    Aparecerá un nuevo proyecto de consola. Una vez creado el proyecto, aparecerá un archivo de origen. Dependiendo del lenguaje que ha elegido, el archivo de código fuente podría denominarse *Program.cs*, *MyThreadWalkthroughApp.cpp*, o *Module1.vb*.

1. Elimine el código que aparece en el archivo de origen y reemplácelo por la lista debajo del código de ejemplo correspondiente.

    ```csharp
    using System;
    using System.Threading;

    public class ServerClass
    {

        static int count = 0;
        // The method that will be called when the thread is started.
        public void InstanceMethod()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            int data = count++;
            // Pause for a moment to provide a delay to make
            // threads more apparent.
            Thread.Sleep(3000);
            Console.WriteLine(
                "The instance method called by the worker thread has ended.");
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 10; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.InstanceMethod));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```C++
    #include "pch.h"
    #include <thread>
    #include <iostream>
    #include <vector>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::cout << "The function called by the worker thread has ended." << std::endl;
    }

    int main() {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doSomeWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
    }

    for (auto& thread : threads) {
        thread.join();
    }

    return 0;
    }
    ```

    ```VB
    Imports System.Threading

    Public Class ServerClass
        ' The method that will be called when the thread is started.
        Public count = 0
        Public Sub InstanceMethod()
            Console.WriteLine(
                    "ServerClass.InstanceMethod is running on another thread.")

            Dim data = count + 1
            ' Pause for a moment to provide a delay to make
            ' threads more apparent.
            Thread.Sleep(3000)
            Console.WriteLine(
                    "The instance method called by the worker thread has ended.")
        End Sub

    End Class

    Public Class Simple

        Public Shared Sub Main()

            Dim ts As New ThreadStarter
            For index = 1 To 10
                ts.CreateThreads()
            Next

        End Sub

    End Class
    Public Class ThreadStarter
        Public Sub CreateThreads()
            Dim serverObject As New ServerClass()

            ' Create the thread object, passing in the
            ' serverObject.InstanceMethod method using a
            ' ThreadStart delegate.
            Dim InstanceCaller As New Thread(AddressOf serverObject.InstanceMethod)

            ' Start the thread.
            InstanceCaller.Start()

            Console.WriteLine("The Main() thread calls this after " _
                        + "starting the new InstanceCaller thread.")

        End Sub
    End Class
    ```

1. En el menú **Archivo**, seleccione **Guardar todo**.

1. (Sólo Visual Basic) En el Explorador de soluciones (panel derecho), haga clic en el nodo del proyecto, elija **propiedades**. En el **aplicación** , modifique la **objeto Startup** a **Simple**.

## <a name="debug-the-multithreaded-app"></a>Depurar la aplicación multiproceso

1. En el editor de código fuente, busque uno de los fragmentos de código siguiente:

    ```csharp
    Thread.Sleep(3000);
    Console.WriteLine();
    ```

    ```C++
    std::this_thread::sleep_for(std::chrono::seconds(3));
    std::cout << "The function called by the worker thread has ended." << std::endl;
    ```

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```

1. Haga clic en el margen interno izquierdo de la `Thread.Sleep` o `std::this_thread::sleep_for` instrucción para insertar un nuevo punto de interrupción.

    En el margen interno, un círculo rojo indica que un punto de interrupción está establecido en esta ubicación.

2. En el **depurar** menú, seleccione **Iniciar depuración** (**F5**).

    Visual Studio compila la solución, la aplicación comienza a ejecutarse con el depurador asociado y, a continuación, se detiene la aplicación en el punto de interrupción.

3. En el editor de código fuente, busque la línea que contiene el punto de interrupción.

### <a name="ShowThreadsInSource"></a>Detectar el marcador de subproceso  

1.  En la barra de herramientas de depuración, seleccione el **Mostrar subprocesos en código fuente** botón ![Mostrar subprocesos en código fuente](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Presione **F11** una vez para avanzar a la línea de un depurador de código.

3.  Examine el margen interno izquierdo de la ventana. En esta línea, verá un *marcador de subproceso* icono ![marcador de subproceso](../debugger/media/dbg-thread-marker.png "ThreadMarker") que es similar a dos subprocesos trenzados. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación.

    Un marcador de subproceso es posible que se ocultan parcialmente por un punto de interrupción.

4.  Desplace el puntero sobre el marcador de subproceso. Una información sobre datos aparece indicando el número de Id. de nombre y el subproceso para cada subproceso detenido. En este caso, el nombre es probablemente `<noname>`.

5.  Seleccione el marcador de subproceso para ver las opciones disponibles en el menú contextual.

### <a name="ParallelStacks"></a>Ver las ubicaciones de subproceso

En el **pilas paralelas** ventana, puede cambiar entre una vista de subprocesos y (para la programación basada en tareas) vista de tareas y se puede ver la información de la pila de llamadas para cada subproceso. En esta aplicación, podemos usar la vista de subprocesos.

1. Abra el **pilas paralelas** ventana eligiendo **depurar** > **Windows** > **pilas paralelas**. Debería ver algo parecido al siguiente. La información exacta variarán según la ubicación actual de cada subproceso, el hardware y el lenguaje de programación.

    ![Ventana Pilas paralelas en](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    En este ejemplo, de izquierda a derecha vemos esta información para el código administrado:

    - Se ha detenido el subproceso principal (izquierda) en `Thread.Start`, donde el punto de detención se indica mediante el icono de marcador de subproceso ![marcador de subproceso](../debugger/media/dbg-thread-marker.png "ThreadMarker").
    - Han escrito dos subprocesos el `ServerClass.InstanceMethod`, uno de los cuales es el subproceso actual (la flecha amarilla), mientras que el otro subproceso ha detenido en `Thread.Sleep`.
    - También se está iniciando un nuevo subproceso (a la derecha), pero se ha detenido en `ThreadHelper.ThreadStart`.

2.  Haga clic en las entradas de la **pilas paralelas** ventana para ver las opciones disponibles en el menú contextual.

    Puede realizar diversas acciones de estos menús contextuales, pero para este tutorial se muestra más de estos detalles en el **inspección paralela** ventana (secciones).

    > [!NOTE]
    > Para ver una lista con información sobre cada subproceso, use el **subprocesos** ventana en su lugar. Consulte [Tutorial: depurar una aplicación multiproceso](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Establece una inspección en una variable

1. Abra el **inspección paralela** ventana seleccionando **depurar** > **Windows** > **inspección paralela**  >  **Inspección 1 paralela**.

2. Seleccione la celda donde verá el `<Add Watch>` texto (o la celda de encabezado vacío en la columna 4) y escriba `data`.

    Los valores de la variable de datos para cada subproceso aparecen en la ventana.

3. Seleccione la celda donde verá el `<Add Watch>` texto (o la celda de encabezado vacío en la columna 5) y escriba `count`.

    Los valores para el `count` variable para cada subproceso aparecen en la ventana. Si no ve esta cantidad de información aún, intente presionar **F11** varias veces para avanzar la ejecución de los subprocesos en el depurador.

    ![Ventana Inspección paralela](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Haga doble clic en una de las filas en la ventana para ver las opciones disponibles.

### <a name="flag-and-unflag-threads"></a>Marcar y desmarcar subprocesos
Puede marcar los subprocesos para realizar un seguimiento de los subprocesos importantes y pasar por alto los demás subprocesos.

1. En el **inspección paralela** ventana, mantenga presionada la **MAYÚS** clave y seleccione varias filas.

2. Haga clic en y seleccione **marca**.

    Se marcan todos los subprocesos seleccionados. Ahora, puede filtrar para mostrar sólo subprocesos marcados.

3.  En el **inspección paralela** ventana, seleccione el **mostrar sólo subprocesos marcados** botón ![Mostrar subprocesos marcados](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").

    Los subprocesos marcados solo aparecen en la lista.

    > [!TIP]
    > Después de que algunos subprocesos marcados, puede haga clic en una línea de código en el editor de código y elija **ejecutar subprocesos marcados al Cursor**. Asegúrese de elegir llegará a todos los subprocesos marcan de código. Visual Studio pausará subprocesos en la línea seleccionada del código, lo que facilita controlar el orden de ejecución por [inmovilizar y reanudar subprocesos](#bkmk_freeze).

4.  Seleccione el **mostrar sólo subprocesos marcados** botón nuevo para volver al **mostrar todos los subprocesos** modo.

5. Para quitar marcadores de subprocesos, haga clic en uno o más subprocesos marcados en el **inspección paralela** ventana y seleccione **Quitar marcador**.

### <a name="bkmk_freeze"></a> Inmovilizar y reanudar la ejecución de subprocesos

> [!TIP]
> Puede inmovilizar y descongelar (suspender y reanudar) los subprocesos para controlar el orden en que subprocesos realizan el trabajo. Esto puede ayudarle a resolver problemas de simultaneidad, como interbloqueos y condiciones de carrera.

1.  En el **inspección paralela** ventana, con todas las filas seleccionadas, secundario y seleccione **inmovilizar**.

    En la segunda columna, aparece un icono de pausa para cada fila. El icono de pausa indica que el subproceso está inmovilizado.

2.  Anule la selección de todas las demás filas seleccionando una sola fila.

3.  Haga clic en una fila y seleccione **reanudar**.

    Desaparece el icono de pausa en esta fila, que indica que el subproceso ya no está inmovilizado.

4.  Cambie al editor de código y presione **F11**. Se ejecuta solo el subproceso no está inmovilizado.

    La aplicación también puede crear instancias de algunos nuevos subprocesos. Todos los nuevos subprocesos son sin marcar y no están inmovilizados.

### <a name="bkmk_follow_a_thread"></a> Siga un único subproceso con puntos de interrupción condicionales

Puede ser útil comprobar la ejecución de un único subproceso en el depurador. Una manera de hacerlo es inmovilizar subprocesos que no está interesado. En algunos escenarios es posible que deberá seguir un único subproceso sin inmovilizar otros subprocesos, por ejemplo, para reproducir un error determinado. Para seguir un subproceso sin inmovilizar otros subprocesos, debe evitar interrumpir el código, excepto en el subproceso que le interesen. Puede hacerlo estableciendo un [punto de interrupción condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Puede establecer puntos de interrupción en distintas condiciones, como el nombre del subproceso o el identificador de subproceso. Puede ser útil es establecer la condición en los datos que sabe que es único para cada subproceso. Se trata de un escenario de depuración comunes, en el que está más interesado en algún valor de datos concreto que en cualquier subproceso en particular.

1. Haga clic en el punto de interrupción creado previamente y seleccione **condiciones**.

2. En el **configuración de punto de interrupción** ventana, escriba `data == 5` para la expresión condicional.

    ![Punto de interrupción condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Si está más interesado en un subproceso concreto, utilice un nombre de subproceso o el Id. de subproceso para la condición. Para hacer esto en el **configuración de punto de interrupción** ventana, seleccione **filtro** en lugar de **expresión condicional**y siga las sugerencias de filtro. Es posible que desee los subprocesos en código de la aplicación, el nombre como identificadores de subprocesos cambian al reiniciar el depurador.

3. Cerrar la **configuración de punto de interrupción** ventana.

4. Seleccione el reinicio ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") botón reiniciar la sesión de depuración.

    Deberá interrumpir el código en el subproceso donde el valor de la variable de datos es 5. En el **inspección paralela** ventana, busque la flecha amarilla que indica el contexto actual del depurador.

5. Ahora, puede saltarse código (**F10**) y avanzar en el código (**F11**) y seguir la ejecución de subproceso único.

    Siempre y cuando la condición de punto de interrupción es única para el subproceso y el depurador no alcanza a cualquier otro punto de interrupción en otros subprocesos (es posible que deba deshabilitarlas), puede ir al código sin tener que cambiar a otros subprocesos y recorrer el código.

    > [!NOTE]
    > Al avanzar el depurador, se ejecutarán todos los subprocesos. Sin embargo, el depurador no interrumpe el código en otros subprocesos a menos que uno de los demás subprocesos alcanza un punto de interrupción.

## <a name="see-also"></a>Vea también

- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Cambio a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Cómo: utilizar la ventana Pila de paralelos](../debugger/using-the-parallel-stacks-window.md)
- [Uso de la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md)