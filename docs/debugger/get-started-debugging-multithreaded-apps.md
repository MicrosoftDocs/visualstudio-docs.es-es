---
title: Proporciona información sobre cómo depurar aplicaciones multiproceso
description: Depurar con las ventanas Inspección paralela y pilas paralelas en Visual Studio
ms.custom: H1HackMay2017
ms.date: 06/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: 62df746b-b0f6-4df4-83cf-b1d9d2e72833
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb178a0a048a3696fc2c1ec642127906c8b83424
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="get-started-debugging-multithreaded-applications-in-visual-studio"></a>Empezar a depurar aplicaciones multiproceso en Visual Studio
Visual Studio proporciona varias herramientas y elementos de la interfaz de usuario para ayudarle a depurar aplicaciones multiproceso. Este tutorial muestra cómo utilizar marcadores de subprocesos, la **pilas paralelas** ventana, el **inspección paralela** ventana, puntos de interrupción condicionales y los puntos de interrupción de filtro. Este tutorial dura sólo unos minutos, pero completarlo, se familiarizará con las características para depurar aplicaciones multiproceso.

|         |         |
|---------|---------|
|  ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo")  |    [Vea un vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) en depuración multiproceso que muestra los pasos similares. |

Otros temas proporcionan información adicional sobre el uso de otras herramientas de depuración multiproceso:

- Para un tema similar que muestra cómo utilizar el **ubicación de depuración** barra de herramientas y la **subprocesos** ventana, consulte [Tutorial: depurar una aplicación multiproceso](../debugger/how-to-use-the-threads-window.md).

- Para un tema similar con un ejemplo que usa <xref:System.Threading.Tasks.Task> (código administrado) y el runtime de simultaneidad (C++), vea [Tutorial: depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md). Para obtener sugerencias de depuración generales que se aplican a los tipos de aplicaciones más multiproceso, leído este tema y el tema vinculado.
  
Para empezar este tutorial, necesita un proyecto de aplicación multiproceso. Siga los pasos que se enumeran a continuación para crear dicho proyecto.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Para crear el proyecto de aplicación multiproceso  
  
1.  En el **archivo** menú, elija **New** y, a continuación, haga clic en **proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
2.  En el **tipo de proyecto**s cuadro, haga clic en el idioma de su elección: **Visual C#**, **Visual C++**, o **Visual Basic**.  
  
3.  En el **plantillas** cuadro, elija **aplicación de consola**.  
  
4.  En el **nombre** cuadro, escriba el nombre MyThreadWalkthroughApp.  
  
5.  Haga clic en **Aceptar**.  
  
     Aparecerá un nuevo proyecto de consola. Una vez creado el proyecto, aparecerá un archivo de código fuente. Dependiendo del lenguaje que ha elegido, el archivo de código fuente podría denominarse Program.cs, MyThreadWalkthroughApp.cpp o Module1.vb.  
  
6.  Elimine el código que aparece en el archivo de origen y reemplácelo por el código de ejemplo que se muestra aquí.

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
    #include "stdafx.h"
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
  
7.  En el **archivo** menú, haga clic en **guardar todo**.  
  
#### <a name="to-begin-the-tutorial"></a>Para comenzar el tutorial  
  
-   En el editor de código fuente, busque el código siguiente: 
  
    ```csharp  
    Thread.Sleep(3000);  
    Console.WriteLine();  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    Console.WriteLine();  
    ```  
    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>Para iniciar la depuración  
  
1.  Haga clic en el margen interno izquierdo de la `Thread.Sleep` o `Thread::Sleep` instrucción para insertar un nuevo punto de interrupción.  
  
     En el margen interno en el lado izquierdo del editor de código fuente, aparece un círculo rojo. Esto indica que ahora hay un punto de interrupción en esa ubicación. 
  
2.  En el **depurar** menú, haga clic en **Iniciar depuración** (**F5**).  
  
     Visual Studio compila la solución, la aplicación comienza a ejecutar con el depurador asociado y, a continuación, la aplicación se detiene en el punto de interrupción.  
  
    > [!NOTE]
    > Si cambiar el foco a la ventana de consola, haga clic en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ventana para devolver el foco a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  En el editor de código fuente, busque la línea que contiene el punto de interrupción:  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    Thread::Sleep(3000);  
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>Para detectar el marcador de subproceso  

1.  En la barra de herramientas Depurar, haga clic en el **Mostrar subprocesos en código fuente** botón ![Mostrar subprocesos en código fuente](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Presione **F11** una vez para avanzar el depurador uno de línea de código.
  
3.  Examine el margen interno izquierdo de la ventana. En esta línea, verá un *marcador de subproceso* icono ![marcador de subproceso](../debugger/media/dbg-thread-marker.png "ThreadMarker") que es similar a dos hilos. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación.

    Tenga en cuenta que un marcador de subproceso puede ocultarse parcialmente por un punto de interrupción. 
  
4.  Desplace el puntero sobre el marcador de subproceso. Aparece la Información sobre datos. En ella se indican el nombre y el número de id. de subproceso de cada subproceso detenido. En este caso, el nombre es probablemente `<noname>`. 
  
5.  Haga clic en el marcador de subproceso para ver las opciones disponibles en el menú contextual.
    
## <a name="ParallelStacks"></a>Ver la ubicación de subprocesos

En el **pilas paralelas** ventana, puede cambiar entre una vista de subprocesos y (para la programación basada en tareas) vista de tareas y se puede ver información de la pila de llamadas para cada subproceso. En esta aplicación, podemos usar la vista de subprocesos.

1. Abra la **pilas paralelas** ventana eligiendo **Depurar > Windows > pilas paralelas**. Debería ver algo parecido a esto (la información exacta que será diferente dependiendo de la ubicación actual de cada subproceso, el hardware y el lenguaje de programación).

    ![Ventana de pilas paralelas](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    En este ejemplo, de izquierda a derecha se obtener esta información:
    
    - El subproceso principal (izquierda) ha detenido en `Thread.Start` (el punto de detención se indica mediante el icono de marcador de subproceso ![marcador de subproceso](../debugger/media/dbg-thread-marker.png "ThreadMarker")).
    - Dos subprocesos han entrado en el `ServerClass.InstanceMethod`, uno de los cuales es el subproceso actual (la flecha amarilla), mientras que el otro subproceso se ha detenido en `Thread.Sleep`.
    - También está iniciando un nuevo subproceso (a la derecha) (detenido en `ThreadHelper.ThreadStart`).

2.  Haga clic en las entradas de la **pilas paralelas** ventana para ver las opciones disponibles en el menú contextual.

    Puede realizar diversas acciones de estos menús contextuales, pero en este tutorial se mostrará más de estos detalles en el **inspección paralela** ventana (secciones siguientes).

    > [!NOTE]
    > Si está más interesado en ver una lista ver con información sobre cada subproceso, utilice el **subprocesos** ventana en su lugar. Vea [Tutorial: depurar una aplicación multiproceso](../debugger/how-to-use-the-threads-window.md).

## <a name="set-a-watch-on-a-variable"></a>Establece una inspección en una Variable

1. Abra la **inspección paralela** ventana eligiendo **Depurar > Windows > inspección paralela > inspección paralela 1**.

2. Haga clic en la celda donde verá el `<Add Watch>` texto (o la celda de encabezado vacía en la columna 4 de mayo), tipo `data`, y presione ENTRAR.

    Los valores de la variable de datos para cada subproceso aparecen en la ventana.

3. Haga clic en nuevo en la celda donde verá el `<Add Watch>` texto (o la celda de encabezado vacía en la columna 5), tipo `count`, y presione ENTRAR.

    Los valores de la variable de recuento para cada subproceso aparecen en la ventana. (Si no ve tanta información todavía, intente presionando F11 varias veces para avanzar la ejecución de los subprocesos en el depurador).

    ![Ventana Inspección paralela](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Haga clic en una de las filas en la ventana para ver las opciones disponibles.

## <a name="flagging-and-unflagging-threads"></a>Marcar y quitar marcadores de subprocesos  
Puede marcar los subprocesos que desea prestar atención especial. Acción de marcar subprocesos es una buena forma de realizar un seguimiento de los subprocesos importantes y obviar los que no le interesan.  
  
#### <a name="to-flag-threads"></a>Para marcar subprocesos  

1. En el **inspección paralela** ventana, mantenga presionada la tecla MAYÚS y seleccione varias filas.

2. Haga clic en y elija **marca**.

    Ahora, se marcan todos los subprocesos seleccionados. Ahora, puede filtrar para mostrar sólo subprocesos marcados.
  
3.  En el **inspección paralela** ventana, busque la **mostrar sólo subprocesos marcados** botón ![Mostrar subprocesos marcados](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
4.  Haga clic en el **mostrar sólo subprocesos marcados** botón.  
  
    Sólo el subproceso marcado aparece ahora en la lista.

    > [!TIP]
    > Cuando se han marcado algunos subprocesos, puede haga clic en una línea de código en el editor de código y elija **ejecutar subprocesos marcados hasta el Cursor** (asegúrese de que elige llegará a todos los subprocesos marcan de código). Esto pausará al número de subprocesos en la línea seleccionada del código, lo que facilita controlar el orden de ejecución por [inmovilizar y reanudar subprocesos](#bkmk_freeze).

5.  Haga clic en el **mostrar sólo subprocesos marcados** botón para volver al **mostrar todos los subprocesos** modo.
    
#### <a name="to-unflag-threads"></a>Para quitar marcadores de subprocesos

Para quitar marcadores de subprocesos, haga clic en uno o varios subprocesos marcados en el **inspección paralela** ventana y elija **Quitar marcador**.

## <a name="bkmk_freeze"></a> Inmovilizar y reanudar la ejecución de subprocesos 

> [!TIP]
> Puede inmovilizar y reanudar (suspender y reanudar) los subprocesos para controlar el orden en el que los subprocesos realizan trabajo. Esto puede ayudarle a resolver problemas de simultaneidad, como interbloqueos y condiciones de anticipación.
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Para inmovilizar y descongelar subprocesos  
  
1.  En el **inspección paralela** ventana, con todas las filas seleccionadas, menú contextual y seleccione **inmovilizar**.

    En la segunda columna, un icono de pausa aparece para cada fila. El icono de pausa indica que el subproceso está inmovilizado.

2.  Anule la selección de las filas, haga clic en una sola fila.

3.  Haga clic en una fila y seleccione **reanudar**.

    El icono de pausa desaparece en esta fila, que indica que el subproceso ya no está inmovilizado.

4.  Cambiar al editor de código y haga clic en **F11**. Solo el subproceso inmovilizado se ejecuta.

    La aplicación también puede crear instancias de algunos de los subprocesos nuevos. Tenga en cuenta que todos los nuevos subprocesos sin marcar y no están inmovilizados.

## <a name="bkmk_follow_a_thread"></a> Siga un subproceso único mediante el uso de puntos de interrupción condicionales

En ocasiones, puede ser útil seguir la ejecución de un único subproceso en el depurador. Una manera para ello consiste en inmovilizar subprocesos que no está interesado en, pero en algunos casos puede que desee seguir un único subproceso sin inmovilizar otros subprocesos (para reproducir un determinado de errores, por ejemplo). Para seguir un subproceso sin inmovilización de otros subprocesos, se debe evitar interrumpir el código excepto en el subproceso que le interesa. Puede hacerlo estableciendo un [punto de interrupción condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Puede establecer puntos de interrupción en condiciones diferentes, como el nombre del subproceso o el identificador de subproceso. Otro método que puede resultar útil consiste en establecer las condiciones en los datos que se sabe que va a ser únicas para cada subproceso. Se trata de un escenario de depuración comunes, en el que está más interesado en algún valor de datos determinado que en un subproceso concreto.

#### <a name="to-follow-a-single-thread"></a>Para seguir un único subproceso

1. Haga clic en el punto de interrupción creado previamente y elija **condiciones**.

2. En el **configuración de punto de interrupción** ventana, escriba `data == 5` para la expresión condicional.

    ![Punto de interrupción condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Si está más interesado en un subproceso concreto, utilice un nombre de subproceso o un identificador de subproceso para la condición. Para hacer esto en el **configuración de punto de interrupción** ventana, seleccione **filtro** en lugar de **expresión condicional**y siga las sugerencias de filtro. Puede que desee entre los subprocesos en código de la aplicación (ya que subprocesos identificadores cambian cuando se reinicie el depurador).

3. Cerrar la **configuración de punto de interrupción** ventana.

4. Haga clic en el reinicio ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") botón para reiniciar la sesión de depuración.

    Se interrumpirá en el código en el subproceso para el que la variable de datos es 5. Busque la flecha amarilla (contexto actual del depurador) el **inspección paralela** ventana para comprobar que.

5. Ahora, puede recorrer el código (F10) y paso a paso en código (F11) y seguimiento de la ejecución del subproceso único.

    Siempre y cuando la condición de punto de interrupción es única para el subproceso y el depurador no alcanza cualquier otro punto de interrupción en otros subprocesos (debe deshabilitarlas), puede recorrer el código y paso a paso en código sin cambiar a otros subprocesos.

    > [!NOTE]
    > Al avanzar el depurador, se ejecutarán todos los subprocesos. Sin embargo, el depurador no interrumpe el código en otros subprocesos a menos que uno de los demás subprocesos llega a un punto de interrupción. 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>Más información acerca de las ventanas de depuración multiproceso 

#### <a name="to-switch-to-another-thread"></a>Para cambiar a otro subproceso 

- Para cambiar a otro subproceso, vea [Cómo: cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>Para obtener más información sobre las ventanas pila paralelas e inspección paralela  
  
- Vea [Cómo: utilizar la ventana Pila paralelas](../debugger/using-the-parallel-stacks-window.md) 

- Vea [Cómo: utilizar la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: Cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)
