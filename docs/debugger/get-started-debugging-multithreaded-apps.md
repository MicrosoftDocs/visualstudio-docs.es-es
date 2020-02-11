---
title: Aprenda a depurar aplicaciones multiproceso
description: Depuración mediante pilas paralelas y ventanas de inspección paralelas en Visual Studio
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
ms.openlocfilehash: 6e21d5174c9a909e9ad8031dfb7585abc52a7e78
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091800"
---
# <a name="get-started-debugging-multithreaded-applications-c-visual-basic-c"></a>Introducción a la depuración de aplicaciones multiproceso (C#, C++Visual Basic,)

Visual Studio proporciona varias herramientas y elementos de la interfaz de usuario para ayudarle a depurar aplicaciones multiproceso. En este tutorial se muestra cómo usar los marcadores de subprocesos, la ventana **pilas paralelas** , la ventana **inspección paralela** , los puntos de interrupción condicionales y los puntos de interrupción del filtro. La realización de este tutorial le permitirá familiarizarse con las características de Visual Studio para la depuración de aplicaciones multiproceso.

Estos dos temas proporcionan información adicional sobre cómo usar otras herramientas de depuración multiproceso:

- Para usar la barra de herramientas **Ubicación de depuración** y la ventana **subprocesos** , vea [Tutorial: depurar una aplicación multiproceso](../debugger/how-to-use-the-threads-window.md).

- Para obtener un ejemplo que usa <xref:System.Threading.Tasks.Task> (código administrado) y el runtime de simultaneidad (C++), consulte [Tutorial: Depuración de una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md). Para obtener sugerencias de depuración generales que se aplican a la mayoría de los tipos de aplicaciones multiproceso, lea este tema y este.

En primer lugar, necesitará un proyecto de aplicación multiproceso. A continuación, encontrará un ejemplo.

## <a name="create-a-multithreaded-app-project"></a>Crear un proyecto de aplicación multiproceso

1. Abra Visual Studio y cree un nuevo proyecto.

   ::: moniker range=">=vs-2019"

   Si la ventana de inicio no está abierta, elija **Archivo** > **Ventana Inicio**.

   En la ventana de inicio, elija **Crear un proyecto nuevo**.

   En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *consola*. A continuación, **C#** elija **C++** , o **Visual Basic** en la lista de idiomas y, a continuación, elija **Windows** en la lista de plataformas. 

   Después de aplicar los filtros de idioma y plataforma, elija la **aplicación de consola (.net Core)** o C++, para, plantilla de **aplicación de consola** y, a continuación, elija **siguiente**.

   > [!NOTE]
   > Si no ve la plantilla correcta, vaya a **herramientas** > **obtener herramientas y características...** , que abre el instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo de escritorio de .NET** o **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

   En la ventana **configurar el nuevo proyecto** , escriba o escriba *MyThreadWalkthroughApp* en el cuadro **nombre del proyecto** . Luego, elija **Crear**.

   ::: moniker-end
   ::: moniker range="vs-2017"
   En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **nuevo proyecto** , elija lo siguiente:

   - En el C# caso de una aplicación, en **C#visual**, elija **escritorio de Windows**y, a continuación, en el panel central, elija aplicación de **consola (.NET Framework)** .
   - En el caso de una aplicación Visual Basic, en **Visual Basic**, elija **escritorio de Windows**y, a continuación, en el panel central, elija **aplicación de consola (.NET Framework)** .
   - En el C++ caso de una aplicación, en **C++visual**, elija **escritorio de Windows**y, a continuación, elija aplicación de consola de **Windows**.

   Si no ve la **aplicación de consola (.net Core)** o, para C++, la plantilla de proyecto de **aplicación de consola** , vaya a **herramientas** > **obtener herramientas y características...** , que abre el instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo de escritorio de .NET** o **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

   A continuación, escriba un nombre como *MyThreadWalkthroughApp* y haga clic en **Aceptar**.

   Seleccione **Aceptar**.
   ::: moniker-end

   Aparecerá un nuevo proyecto de consola. Una vez creado el proyecto, aparece un archivo de código fuente. Dependiendo del lenguaje que haya elegido, el archivo de código fuente podría llamarse *Program.CS*, *MyThreadWalkthroughApp. cpp*o *Module1. VB*.

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

1. (Solo Visual Basic) En Explorador de soluciones (panel derecho), haga clic con el botón secundario en el nodo del proyecto, elija **propiedades**. En la pestaña **aplicación** , cambie el **objeto startup** a **simple**.

## <a name="debug-the-multithreaded-app"></a>Depurar la aplicación multiproceso

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

1. Haga clic con el botón primario en el margen interno izquierdo de la instrucción `Thread.Sleep` o `std::this_thread::sleep_for` para insertar un nuevo punto de interrupción.

    En el medianil, un círculo rojo indica que se ha establecido un punto de interrupción en esta ubicación.

2. En el menú **depurar** , seleccione **iniciar depuración** (**F5**).

    Visual Studio compila la solución, la aplicación comienza a ejecutarse con el depurador adjunto y, a continuación, la aplicación se detiene en el punto de interrupción.

3. En el editor de código fuente, busque la línea que contiene el punto de interrupción.

### <a name="ShowThreadsInSource"></a>Detección del marcador de subproceso  

1. En la barra de herramientas Depurar, seleccione el botón **Mostrar subprocesos en el origen** ![Mostrar los subprocesos en el origen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Presione **F11** una vez para avanzar el depurador una línea de código.

3. Examine el margen interno izquierdo de la ventana. En esta línea, verá un icono de *marcador de subproceso* que se asemeja a dos ![subprocesos](../debugger/media/dbg-thread-marker.png "ThreadMarker") retorcidos. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación.

    Un punto de interrupción puede ocultar parcialmente un marcador de subproceso.

4. Desplace el puntero sobre el marcador de subproceso. Aparece una información sobre información que indica el nombre y el número de identificación del subproceso para cada subproceso detenido. En este caso, es probable que el nombre sea `<noname>`.

5. Seleccione el marcador de subproceso para ver las opciones disponibles en el menú contextual.

### <a name="ParallelStacks"></a>Ver las ubicaciones de los subprocesos

En la ventana **pilas paralelas** , puede cambiar entre una vista de subprocesos y la vista de tareas (para la programación basada en tareas), y puede ver la información de la pila de llamadas de cada subproceso. En esta aplicación, podemos usar la vista de subprocesos.

1. Abra la ventana **pilas paralelas** eligiendo **depurar** > **Windows** > **pilas paralelas**. Debería ver algo parecido a lo siguiente. La información exacta variará en función de la ubicación actual de cada subproceso, el hardware y el lenguaje de programación.

    ![Ventana pilas paralelas](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    En este ejemplo, de izquierda a derecha, vemos esta información para código administrado:

    - El subproceso principal (lado izquierdo) se ha detenido en `Thread.Start`, donde el punto de detención lo indica el ![marcador](../debugger/media/dbg-thread-marker.png "ThreadMarker")de subproceso del icono de marcador de subproceso.
    - Dos subprocesos han entrado en el `ServerClass.InstanceMethod`, uno de los cuales es el subproceso actual (flecha amarilla), mientras que el otro subproceso se ha detenido en `Thread.Sleep`.
    - También se inicia un nuevo subproceso (a la derecha), pero se detiene en `ThreadHelper.ThreadStart`.

2. Haga clic con el botón secundario en entradas en la ventana **pilas paralelas** para ver las opciones disponibles en el menú contextual.

    Puede realizar varias acciones en estos menús contextuales, pero para este tutorial se mostrarán más detalles en la ventana **inspección paralela** (secciones siguientes).

    > [!NOTE]
    > Para ver una vista de lista con información sobre cada subproceso, utilice en su lugar la ventana **subprocesos** . Vea [Tutorial: depurar una aplicación multiproceso](../debugger/how-to-use-the-threads-window.md).

### <a name="set-a-watch-on-a-variable"></a>Establecer un reloj en una variable

1. Abra la ventana **inspección paralela** seleccionando **depurar** > **Windows** > la **inspección paralela** > la **inspección paralela 1**.

2. Seleccione la celda en la que verá el `<Add Watch>` texto (o la celda de encabezado vacía en la columna 4) y escriba `data`.

    Los valores de la variable de datos para cada subproceso aparecen en la ventana de.

3. Seleccione la celda en la que verá el `<Add Watch>` texto (o la celda de encabezado vacía en la quinta columna) y escriba `count`.

    Los valores de la variable `count` para cada subproceso aparecen en la ventana de. Si aún no ve esta cantidad de información, intente presionar **F11** algunas veces para avanzar la ejecución de los subprocesos en el depurador.

    ![Ventana Inspección paralela](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Haga clic con el botón secundario en una de las filas de la ventana para ver las opciones disponibles.

### <a name="flag-and-unflag-threads"></a>Marcar y desmarcar subprocesos
Puede marcar los subprocesos para realizar un seguimiento de los subprocesos importantes y omitir los demás subprocesos.

1. En la ventana **inspección paralela** , mantenga presionada la tecla **MAYÚS** y seleccione varias filas.

2. Haga clic con el botón derecho y seleccione **marca**.

    Se marcan todos los subprocesos seleccionados. Ahora, puede filtrar para mostrar solo los subprocesos marcados.

3. En la ventana **inspección paralela** , seleccione el botón **Mostrar solo subprocesos marcados** Mostrar subprocesos ![marcados](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").

    Solo los subprocesos marcados aparecen en la lista.

    > [!TIP]
    > Después de haber marcado algunos subprocesos, puede hacer clic con el botón secundario en una línea de código en el editor de código y elegir **Ejecutar subprocesos marcados hasta el cursor**. Asegúrese de elegir el código al que se encontrarán todos los subprocesos marcados. Visual Studio pausará los subprocesos en la línea de código seleccionada, lo que facilita el control del orden de ejecución al [inmovilizar y reanudar los subprocesos](#bkmk_freeze).

4. Seleccione el botón **Mostrar solo subprocesos marcados** de nuevo para volver al modo **Mostrar todos los subprocesos** .

5. Para quitar los marcadores de subprocesos, haga clic con el botón derecho en uno o más subprocesos marcados en la ventana **inspección paralela** y seleccione **Quitar marcador**.

### <a name="bkmk_freeze"></a>Inmovilizar y reanudar la ejecución de subprocesos

> [!TIP]
> Puede inmovilizar y reanudar los subprocesos (suspender y reanudar) para controlar el orden en el que los subprocesos realizan el trabajo. Esto puede ayudarle a resolver problemas de simultaneidad como interbloqueos y condiciones de carrera.

1. En la ventana **inspección paralela** , con todas las filas seleccionadas, haga clic con el botón secundario y seleccione **inmovilizar**.

    En la segunda columna, aparece un icono de pausa para cada fila. El icono de pausa indica que el subproceso está inmovilizado.

2. Anule la selección de todas las demás filas seleccionando solo una fila.

3. Haga clic con el botón secundario en una fila y seleccione **reanudar**.

    El icono de pausa desaparece de esta fila, lo que indica que el subproceso ya no está inmovilizado.

4. Cambie al editor de código y presione **F11**. Solo se ejecuta el subproceso inmovilizado.

    La aplicación también puede crear instancias de algunos subprocesos nuevos. Los nuevos subprocesos no están marcados y no están inmovilizados.

### <a name="bkmk_follow_a_thread"></a>Seguir un solo subproceso con puntos de interrupción condicionales

Puede ser útil seguir la ejecución de un único subproceso en el depurador. Una forma de hacerlo es inmovilizar los subprocesos que no le interesan. En algunos escenarios es posible que tenga que seguir un único subproceso sin inmovilizar otros subprocesos, por ejemplo, para reproducir un error determinado. Para seguir un subproceso sin inmovilizar otros subprocesos, debe evitar interrumpir el código, excepto en el subproceso en el que está interesado. Puede hacerlo estableciendo un [punto de interrupción condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Puede establecer puntos de interrupción en condiciones diferentes, como el nombre del subproceso o el identificador del subproceso. Puede ser útil establecer la condición en los datos que sabe que son únicos para cada subproceso. Se trata de un escenario de depuración común, en el que está más interesado en algunos valores de datos concretos que en un subproceso determinado.

1. Haga clic con el botón secundario en el punto de interrupción que creó anteriormente y seleccione **condiciones**.

2. En la ventana **configuración del punto de interrupción** , escriba `data == 5` para la expresión condicional.

    ![Punto de interrupción condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Si está más interesado en un subproceso concreto, use un nombre de subproceso o un identificador de subproceso para la condición. Para hacer esto en la ventana **configuración del punto de interrupción** , seleccione **filtrar** en lugar de **expresión condicional**y siga las sugerencias de filtro. Es posible que desee asignar un nombre a los subprocesos del código de la aplicación, ya que los identificadores de subprocesos cambian al reiniciar el depurador.

3. Cierre la ventana de **configuración del punto de interrupción** .

4. Seleccione el botón reiniciar la ![aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") para reiniciar la sesión de depuración.

    Interrumpirá el código en el subproceso en el que el valor de la variable de datos es 5. En la ventana **inspección paralela** , busque la flecha amarilla que indica el contexto del depurador actual.

5. Ahora, puede depurar paso a paso por procedimientos (**F10**) y depurar paso a paso por instrucciones el código (**F11**) y seguir la ejecución de un único subproceso.

    Siempre y cuando la condición de punto de interrupción sea única para el subproceso, y el depurador no alcance ningún otro punto de interrupción en otros subprocesos (puede que tenga que deshabilitarlos), puede desplazarse por el código y ejecutar paso a paso el código sin cambiar a otros subprocesos.

    > [!NOTE]
    > Al avanzar el depurador, se ejecutarán todos los subprocesos. Sin embargo, el depurador no interrumpirá el código en otros subprocesos a menos que uno de los otros subprocesos llegue a un punto de interrupción.

## <a name="see-also"></a>Consulte también

- [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Cambio a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)
- [Cómo: usar la ventana de pila paralela](../debugger/using-the-parallel-stacks-window.md)
- [Uso de la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md)