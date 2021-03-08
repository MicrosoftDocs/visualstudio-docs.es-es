---
title: Información sobre la depuración de aplicaciones multiproceso
description: Depuración mediante las ventanas Pilas paralelas e Inspección paralela en Visual Studio
ms.custom: ''
ms.date: 02/14/2020
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bc5232d616466ec5aa0916d5d1ad9e7bd5b1247c
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101684117"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Introducción a la depuración de aplicaciones multiproceso (C#, Visual Basic, C++)

Visual Studio proporciona varias herramientas y elementos de la interfaz de usuario para ayudarle a depurar aplicaciones multiproceso. En este tutorial se muestra cómo usar marcadores de subprocesos, la ventanas **Pilas paralelas** e **Inspección paralela**, y los puntos de interrupción condicionales y de filtro. Al finalizar este tutorial se habrá familiarizado con las características de Visual Studio para la depuración de aplicaciones multiproceso.

En estos dos temas se proporciona información adicional sobre cómo usar otras herramientas de depuración multiproceso:

- Para usar la barra de herramientas **Ubicación de depuración** y la ventana **Subprocesos**, vea [Tutorial: Depuración de una aplicación multiproceso](../debugger/how-to-use-the-threads-window.md).

- Para obtener un ejemplo en el que se usa <xref:System.Threading.Tasks.Task> (código administrado) y el runtime de simultaneidad (C++), vea [Tutorial: Depuración de una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md). Para obtener sugerencias de depuración generales que se aplican a la mayoría de los tipos de aplicaciones multiproceso, lea ese tema y este.

En primer lugar, necesitará un proyecto de aplicación multiproceso. A continuación se muestra un ejemplo.

## <a name="create-a-multithreaded-app-project"></a>Creación de un proyecto de aplicación multiproceso

1. Abra Visual Studio y cree un nuevo proyecto.

   ::: moniker range=">=vs-2019"

   Si la ventana de inicio no está abierta, elija **Archivo** > **Ventana Inicio**.

   En la ventana de inicio, elija **Crear un proyecto nuevo**.

   En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *consola*. Seguidamente, elija **C#** , **C++** o **Visual Basic** en la lista Lenguajes y, luego, **Windows** en la lista Plataformas. 

   Después de aplicar los filtros de lenguaje y plataforma, elija la plantilla **Aplicación de consola** para .NET Core o C++ y luego elija **Siguiente**.

   > [!NOTE]
   > Si no ve la plantilla correcta, vaya a **Herramientas** > **Obtener herramientas y características...** para abrir el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** o **Desarrollo para el escritorio con C++** y, después, elija **Modificar**.

   En la ventana **Configurar el nuevo proyecto**, escriba *MyThreadWalkthroughApp* en el cuadro **Nombre del proyecto**. A continuación, elija **Siguiente** o **Crear**, sea cual sea la opción que esté disponible.

   Para un proyecto .NET Core, elija la plataforma de destino recomendada (.NET Core 3.1) o .NET 5 y luego elija **Crear**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, elija lo siguiente:

   - Para una aplicación de C#, en **Visual C#** , elija **Escritorio de Windows** y, después, en el panel central, **Aplicación de consola (.NET Framework)** .
   - Para una aplicación de Visual Basic, en **Visual Basic**, elija **Escritorio de Windows** y, después, en el panel central, **Aplicación de consola (.NET Framework)** .
   - Para una aplicación de C++, en **Visual C++** , elija **Escritorio de Windows** y después, **Aplicación de consola Windows**.

   Si no ve la plantilla de proyecto **Aplicación de consola (.NET Framework)** o, para C++, **Aplicación de consola**, vaya a **Herramientas** > **Obtener herramientas y características…** para abrir el Instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo de escritorio de .NET** o **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

   Luego escriba un nombre como *MyThreadWalkthroughApp* y haga clic en **Aceptar**.

   Seleccione **Aceptar**.
   ::: moniker-end

   Aparecerá un nuevo proyecto de consola. Una vez que se ha creado el proyecto, aparece un archivo de código fuente. En función del lenguaje elegido, el archivo de código fuente se podría denominar *Program.cs*, *MyThreadWalkthroughApp.cpp* o *Module1.vb*.

1. Elimine el código que aparece en el archivo de código fuente y reemplácelo por la siguiente lista de códigos de ejemplo adecuada.

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
                "The instance method called by the worker thread has ended. " + data);
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
    // #include "pch.h" // Use with pre-compiled header
    #include <thread>
    #include <iostream>
    #include <vector>
    #include <string>

    int count = 0;

    void doSomeWork() {

        std::cout << "The doSomeWork function is running on another thread." << std::endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        std::this_thread::sleep_for(std::chrono::seconds(3));
        std::string str = std::to_string(data);
        std::cout << "The function called by the worker thread has ended. " + str<< std::endl;
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
                    "The instance method called by the worker thread has ended. " + data)
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

1. (Solo para Visual Basic) En el Explorador de soluciones (panel de la derecha), haga clic con el botón derecho en el nodo del proyecto y seleccione **Propiedades**. En la pestaña **Aplicación**, cambie **Objeto de inicio** a **Simple**.

## <a name="debug-the-multithreaded-app"></a>Depuración de la aplicación multiproceso

1. En el editor de código fuente, busque uno de los fragmentos de código siguientes:

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

1. Haga clic en el margen izquierdo de la instrucción `Thread.Sleep` o `std::this_thread::sleep_for` para insertar un nuevo punto de interrupción.

    En el margen, un círculo de color rojo indica que se ha establecido un punto de interrupción en esa ubicación.

2. En el menú **Depurar**, seleccione **Iniciar depuración** (**F5**).

    Visual Studio compila la solución, la aplicación comienza a ejecutarse con el depurador adjunto y, después, se detiene en el punto de interrupción.

3. En el editor de código fuente, busque la línea que contiene el punto de interrupción.

### <a name="discover-the-thread-marker"></a><a name="ShowThreadsInSource"></a>Detección del marcador de subproceso  

1. En la barra de herramientas de depuración, seleccione el botón **Mostrar subprocesos en código fuente** ![Show Threads in Source](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Presione **F11** una vez para que el depurador avance una línea de código.

3. Examine el margen interno izquierdo de la ventana. En esta línea, verá un icono de *marcador de subproceso* ![Thread Marker](../debugger/media/dbg-thread-marker.png "ThreadMarker") que se parece a dos hilos entrelazados. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación.

    Un punto de interrupción puede ocultar parcialmente un marcador de subproceso.

4. Desplace el puntero sobre el marcador de subproceso. Aparece una sugerencia de datos en la que se indican el nombre y el número de id. de subproceso de cada subproceso detenido. En este caso, el nombre probablemente sea `<noname>`.

5. Seleccione el marcador de subproceso para ver las opciones disponibles en el menú contextual.

### <a name="view-the-thread-locations"></a><a name="ParallelStacks"></a>Visualización de ubicaciones de subprocesos

En la ventana **Pilas paralelas**, puede cambiar entre una vista Subprocesos y (para la programación basada en tareas) la vista Tareas, y ver la información de la pila de llamadas de cada subproceso. En esta aplicación, se puede usar la vista Subprocesos.

1. Para abrir la ventana **Pilas paralelas**, seleccione **Depurar** > **Ventanas** > **Pilas paralelas**. Debería ver algo parecido a lo siguiente. La información exacta variará en función de la ubicación actual de cada subproceso, el hardware y el lenguaje de programación.

    ![Ventana Pilas paralelas](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    En este ejemplo, de izquierda a derecha, se ve esta información para código administrado:

    - El subproceso principal (lado izquierdo) se ha detenido en `Thread.Start`, donde el punto de detención se indica mediante el icono de marcador de subproceso ![Thread Marker](../debugger/media/dbg-thread-marker.png "ThreadMarker").
    - Dos subprocesos han entrado en `ServerClass.InstanceMethod`; uno de ellos es el subproceso actual (flecha amarilla), mientras que el otro se ha detenido en `Thread.Sleep`.
    - También se inicia un nuevo subproceso (a la derecha), pero se detiene en `ThreadHelper.ThreadStart`.

2. Haga clic con el botón derecho en las entradas de la ventana **Pilas paralelas** para ver las opciones disponibles en el menú contextual.

    Puede realizar varias acciones desde estos menús contextuales, pero para este tutorial, se mostrarán más detalles en la ventana **Inspección paralela** (secciones siguientes).

    > [!NOTE]
    > Para ver una vista de lista con información sobre cada subproceso, use en su lugar la ventana **Subprocesos**. Vea [Tutorial: Depuración de una aplicación multiproceso](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Establecimiento de una inspección en una variable

1. Para abrir la ventana **Inspección paralela**, seleccione **Depurar** > **Ventanas** > **Inspección paralela** > **Inspección paralela 1**.

2. Seleccione la celda en la que se ve el texto `<Add Watch>` (o la celda de encabezado vacía en la columna 4) y escriba `data`.

    En la ventana aparecerán los valores de la variable de datos para cada subproceso.

3. Seleccione la celda en la que se ve el texto `<Add Watch>` (o la celda de encabezado vacía en la columna 5) y escriba `count`.

    En la ventana aparecerán los valores de la variable `count` de datos para cada subproceso. Si todavía no ve mucha información, intente presionar **F11** varias veces para avanzar la ejecución de los subprocesos en el depurador.

    ![Ventana Inspección paralela](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Haga clic con el botón derecho en una de las filas de la ventana para ver las opciones disponibles.

### <a name="flag-and-unflag-threads"></a>Marcar y desmarcar subprocesos
Puede marcar los subprocesos para realizar el seguimiento de los importantes y omitir el resto.

1. En la ventana **Inspección paralela**, mantenga presionada la tecla **Mayús** y seleccione varias filas.

2. Haga clic con el botón derecho y seleccione **Marcar**.

    Se marcarán todos los subprocesos seleccionados. Ahora, puede filtrar para mostrar solo los subprocesos marcados.

3. En la ventana **Inspección paralela**, seleccione el botón **Mostrar solo los subprocesos marcados** ![Show Flagged Threads](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").

    En la lista solo aparecerán los subprocesos marcados.

    > [!TIP]
    > Después de haber marcado algunos subprocesos, puede hacer clic con el botón derecho en una línea de código en el editor de código y elegir **Ejecutar subprocesos marcados hasta el cursor**. Asegúrese de elegir código al que accedan todos los subprocesos marcados. Visual Studio pausará los subprocesos en la línea de código seleccionada, lo que facilita el control del orden de ejecución mediante la [inmovilización y reanudación de los subprocesos](#bkmk_freeze).

4. Vuelva a seleccionar el botón **Mostrar solo subprocesos marcados** para activar de nuevo el modo **Mostrar todos los subprocesos**.

5. Para quitar los marcadores de subprocesos, haga clic con el botón derecho en uno o más subprocesos marcados en la ventana **Inspección paralela** y seleccione **Quitar marca**.

### <a name="freeze-and-thaw-thread-execution"></a><a name="bkmk_freeze"></a> Inmovilización y reanudación de la ejecución de subprocesos

> [!TIP]
> Puede inmovilizar y reanudar los subprocesos (suspenderlos y reanudarlos) para controlar el orden en el que realizan el trabajo. Esto puede ayudarle a resolver incidencias de simultaneidad como interbloqueos y condiciones de carrera.

1. En la ventana **Inspección paralela**, con todas las filas seleccionadas, haga clic con el botón derecho y seleccione **Inmovilizar**.

    En la segunda columna, aparece un icono de pausa para cada fila. El icono de pausa indica que el subproceso está inmovilizado.

2. Para anular la selección de todas las filas restantes, seleccione solo una.

3. Haga clic con el botón derecho en una fila y seleccione **Reanudar**.

    El icono de pausa desaparece de esta fila, lo que indica que el subproceso ya no está inmovilizado.

4. Cambie al editor de código y presione **F11**. Solo se ejecuta el subproceso inmovilizado.

    Es posible que la aplicación también cree instancias de algunos subprocesos nuevos. Los subprocesos nuevos no están marcados ni se inmovilizan.

### <a name="follow-a-single-thread-with-conditional-breakpoints"></a><a name="bkmk_follow_a_thread"></a> Seguimiento de un solo subproceso con puntos de interrupción condicionales

Puede ser útil seguir la ejecución de un único subproceso en el depurador. Una forma de hacerlo consiste en inmovilizar los subprocesos que no le interesan. En algunos escenarios, es posible que tenga que seguir un único subproceso sin inmovilizar el resto, por ejemplo, para reproducir un error determinado. Para seguir un subproceso sin inmovilizar los demás, debe evitar interrumpir el código, excepto en el subproceso que le interese. Para ello, puede establecer un [punto de interrupción condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Puede establecer puntos de interrupción en función de diferentes condiciones, como el nombre o el identificador del subproceso. Puede ser útil establecer la condición en los datos que sabe que son únicos para cada subproceso. Se trata de un escenario de depuración común, en el que está más interesado en valores de datos concretos que en un subproceso determinado.

1. Haga clic con el botón derecho en el punto de interrupción que ha creado antes y seleccione **Condiciones**.

2. En la ventana **Configuración del punto de interrupción**, escriba `data == 5` para la expresión condicional.

    ![Punto de interrupción condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Si está más interesado en un subproceso concreto, use un nombre o un identificador de subproceso para la condición. Para hacer esto en la ventana **Configuración del punto de interrupción**, seleccione **Filtro** en lugar de **Expresión condicional** y siga las sugerencias de filtro. Es posible que quiera asignar un nombre a los subprocesos del código de la aplicación, ya que los identificadores de subprocesos cambian al reiniciar el depurador.

3. Cierre la ventana **Configuración del punto de interrupción**.

4. Seleccione el botón Reiniciar ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") para reiniciar la sesión de depuración.

    Interrumpirá el código en el subproceso en el que el valor de la variable de datos es 5. En la ventana **Inspección paralela**, busque la flecha de color amarillo que indica el contexto del depurador actual.

5. Ahora, puede depurar el código paso a paso por procedimientos (**F10**) y paso a paso por instrucciones (**F11**), y seguir la ejecución del subproceso único.

    Siempre y cuando la condición de punto de interrupción sea única para el subproceso, y el depurador no alcance ningún otro punto de interrupción en otros subprocesos (es posible que tenga que deshabilitarlos), puede depurar el código paso a paso por procedimientos y por instrucciones sin cambiar a otros subprocesos.

    > [!NOTE]
    > Al avanzar el depurador, se ejecutarán todos los subprocesos. Pero el depurador no interrumpirá el código en otros subprocesos a menos que uno llegue a un punto de interrupción.

## <a name="see-also"></a>Vea también

- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Cómo: cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Cómo: Usar la ventana Pila paralela](../debugger/using-the-parallel-stacks-window.md)
- [Cómo: Uso de la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md)