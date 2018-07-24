---
title: Obtenga información sobre cómo depurar aplicaciones multiproceso
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
ms.openlocfilehash: a037ef99a7e1ea56f6535b99b533c1c723fd2d81
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204224"
---
# <a name="get-started-debugging-multithreaded-applications-in-visual-studio"></a>Empezar a depurar aplicaciones multiproceso en Visual Studio
Visual Studio proporciona varias herramientas y elementos de interfaz de usuario para ayudar a depurar aplicaciones multiproceso. Este tutorial muestra cómo usar los marcadores de subprocesos, el **pilas paralelas** ventana, el **inspección paralela** ventana puntos de interrupción condicionales y los puntos de interrupción de filtro. En este tutorial tarda solo unos minutos, pero completarlo, se familiarizará con las características para depurar aplicaciones multiproceso.

|         |         |
|---------|---------|
|  ![icono de cámara de película para vídeo](../install/media/video-icon.png "Ver un vídeo")  |    [Vea un vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Debugging-Multi-threaded-Apps-in-Visual-Studio-2017-MoZPKMD6D_111787171) sobre la depuración multiproceso que se muestran los mismos pasos. |

Otros temas proporcionan información adicional sobre el uso de otras herramientas de depuración multiproceso:

- Un tema similar que se muestra cómo usar el **ubicación de depuración** barra de herramientas y la **subprocesos** ventana, consulte [Tutorial: depurar una aplicación multiproceso](../debugger/how-to-use-the-threads-window.md).

- Para un tema similar con un ejemplo que usa <xref:System.Threading.Tasks.Task> (código administrado) y el runtime de simultaneidad (C++), consulte [Tutorial: depurar una aplicación paralela](../debugger/walkthrough-debugging-a-parallel-application.md). Para sugerencias de depuración generales que se aplican a los tipos de aplicaciones multiproceso más, lea este tema y el tema vinculado.
  
Para empezar este tutorial, necesita un proyecto de aplicación multiproceso. Siga los pasos que se enumeran a continuación para crear dicho proyecto.  
  
#### <a name="to-create-the-multithreaded-app-project"></a>Para crear el proyecto de aplicación multiproceso  
  
1.  En el **archivo** menú, elija **New** y, a continuación, haga clic en **proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
2.  En el **tipo de proyecto**s cuadro, haga clic en el idioma que prefiera: **Visual C#**, **Visual C++**, o **Visual Basic**.  
  
3.  En el **plantillas** , seleccione **aplicación de consola**.  
  
4.  En el **nombre** cuadro, escriba el nombre MyThreadWalkthroughApp.  
  
5.  Haga clic en **Aceptar**.  
  
     Aparecerá un nuevo proyecto de consola. Una vez creado el proyecto, aparecerá un archivo de código fuente. Dependiendo del lenguaje que ha elegido, el archivo de código fuente podría denominarse Module1.vb, MyThreadWalkthroughApp.cpp o Program.cs.  
  
6.  Elimine el código que aparece en el archivo de origen y reemplazarlo por el código de ejemplo que se muestra aquí.

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

    using namespace;

    int count = 0;

    void doSomeWork() {

        cout << "The doSomeWork function is running on another thread." << endl;
        int data = count++;
        // Pause for a moment to provide a delay to make
        // threads more apparent.
        this_thread::sleep_for(chrono::seconds(3));
        cout << "The function called by the worker thread has ended." << endl;
    }

    int main() {
        vector<thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(thread(doSomeWork));
            cout << "The Main() thread calls this after starting the new thread" << endl;
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
    this_thread::sleep_for(chrono::seconds(3));
    cout << "The function called by the worker thread has ended." << endl; 
    ```  

    ```VB
    Thread.Sleep(3000)
    Console.WriteLine()
    ```
  
#### <a name="to-start-debugging"></a>Para iniciar la depuración  
  
1.  Haga clic en el margen interno izquierdo de la `Thread.Sleep` o `this_thread::sleep_for` instrucción para insertar un nuevo punto de interrupción.  
  
     En el margen interno en el lado izquierdo del editor de código fuente, aparece un círculo rojo. Esto indica que ahora hay un punto de interrupción en esa ubicación. 
  
2.  En el **depurar** menú, haga clic en **Iniciar depuración** (**F5**).  
  
     Visual Studio compila la solución, la aplicación comienza a ejecutarse con el depurador asociado y, a continuación, se detiene la aplicación en el punto de interrupción.  
  
    > [!NOTE]
    > Si cambia el foco a la ventana de consola, haga clic en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ventana para devolver el foco a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  En el editor de código fuente, busque la línea que contiene el punto de interrupción:  
  
    ```csharp  
    Thread.Sleep(3000);  
    ```  
  
    ```C++  
    this_thread::sleep_for(chrono::seconds(3)); 
    ```

    ```VB
    Thread.Sleep(3000)
    ```    
  
#### <a name="ShowThreadsInSource"></a>Para detectar el marcador de subproceso  

1.  En la barra de herramientas Depurar, haga clic en el **Mostrar subprocesos en código fuente** botón ![Mostrar subprocesos en código fuente](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker").

2. Presione **F11** una vez para avanzar a la línea de un depurador de código.
  
3.  Examine el margen interno izquierdo de la ventana. En esta línea, verá un *marcador de subproceso* icono ![marcador de subproceso](../debugger/media/dbg-thread-marker.png "ThreadMarker") que es similar a dos hilos. El marcador de subproceso indica que un subproceso se ha detenido en esa ubicación.

    Tenga en cuenta que un marcador de subproceso es posible que se ocultan parcialmente por un punto de interrupción. 
  
4.  Desplace el puntero sobre el marcador de subproceso. Aparece la Información sobre datos. En ella se indican el nombre y el número de id. de subproceso de cada subproceso detenido. En este caso, el nombre es probablemente `<noname>`. 
  
5.  Haga clic en el marcador de subproceso para ver las opciones disponibles en el menú contextual.
    
## <a name="ParallelStacks"></a>Ver la ubicación de subprocesos

En el **pilas paralelas** ventana, puede cambiar entre una vista de subprocesos y (para la programación basada en tareas) vista de tareas y se puede ver la información de la pila de llamadas para cada subproceso. En esta aplicación, podemos usar la vista de subprocesos.

1. Abra el **pilas paralelas** ventana eligiendo **Depurar > Windows > pilas paralelas**. Debería ver algo parecido a esto (la información exacta será diferente dependiendo de la ubicación actual de cada subproceso, el hardware y el lenguaje de programación).

    ![Ventana Pilas paralelas en](../debugger/media/dbg-multithreaded-parallel-stacks.png "ParallelStacksWindow")

    En este ejemplo, de izquierda a derecha obtenemos esta información para el código administrado:
    
    - Se ha detenido el subproceso principal (izquierda) en `Thread.Start` (el punto de detención se indica mediante el icono de marcador de subproceso ![marcador de subproceso](../debugger/media/dbg-thread-marker.png "ThreadMarker")).
    - Han escrito dos subprocesos el `ServerClass.InstanceMethod`, uno de los cuales es el subproceso actual (la flecha amarilla), mientras que el otro subproceso ha detenido en `Thread.Sleep`.
    - También se inicia un subproceso nuevo (a la derecha) (detenido en `ThreadHelper.ThreadStart`).

2.  Haga clic en las entradas de la **pilas paralelas** ventana para ver las opciones disponibles en el menú contextual.

    Puede realizar diversas acciones de estos menús contextuales, pero para este tutorial se muestra más de estos detalles en el **inspección paralela** ventana (secciones).

    > [!NOTE]
    > Si está más interesado en ver una lista de ver información sobre cada subproceso, utilice el **subprocesos** ventana en su lugar. Consulte [Tutorial: depurar una aplicación multiproceso](../debugger/how-to-use-the-threads-window.md).

## <a name="set-a-watch-on-a-variable"></a>Establece una inspección en una Variable

1. Abra el **inspección paralela** ventana eligiendo **Depurar > Windows > inspección paralela > inspección paralela 1**.

2. Haga clic en la celda donde verá el `<Add Watch>` texto (o la celda de encabezado vacío en la columna 4 de mayo), tipo `data`, y presione ENTRAR.

    Los valores de la variable de datos para cada subproceso aparecen en la ventana.

3. Haga clic de nuevo en la celda donde verá el `<Add Watch>` texto (o la celda de encabezado vacío en la columna 5), tipo `count`, y presione ENTRAR.

    Los valores de la variable de contador para cada subproceso aparecen en la ventana. (Si no ve esta cantidad de información aún, intente presionar F11 varias veces para avanzar la ejecución de los subprocesos en el depurador).

    ![Ventana Inspección paralela](../debugger/media/dbg-multithreaded-parallel-watch.png "ParallelWatchWindow")

4. Haga clic en una de las filas en la ventana para ver las opciones disponibles.

## <a name="flagging-and-unflagging-threads"></a>Marcar y quitar marcadores de subprocesos  
Puede marcar los subprocesos que desee prestar atención especial. Acción de marcar subprocesos es una buena manera para realizar un seguimiento de los subprocesos importantes y obviar los que no le interesen.  
  
#### <a name="to-flag-threads"></a>Para marcar subprocesos  

1. En el **inspección paralela** ventana, mantenga presionada la tecla MAYÚS y seleccione varias filas.

2. Haga clic en y elija **marca**.

    Ahora, se marcan todos los subprocesos seleccionados. Ahora, puede filtrar para mostrar sólo subprocesos marcados.
  
3.  En el **inspección paralela** ventana, busque la **mostrar sólo subprocesos marcados** botón ![Mostrar subprocesos marcados](../debugger/media/dbg-threads-show-flagged.png "ThreadMarker").  
  
4.  Haga clic en el **mostrar sólo subprocesos marcados** botón.  
  
    Sólo el subproceso marcado aparece ahora en la lista.

    > [!TIP]
    > Cuando algunos subprocesos marcados, puede haga clic en una línea de código en el editor de código y elija **ejecutar subprocesos marcados al Cursor** (asegúrese de que elige llegará a todos los subprocesos marcan de código). Esto pondrá en pausa los subprocesos en la línea seleccionada del código, lo que facilita controlar el orden de ejecución por [inmovilizar y reanudar subprocesos](#bkmk_freeze).

5.  Haga clic en el **mostrar sólo subprocesos marcados** botón para volver al **mostrar todos los subprocesos** modo.
    
#### <a name="to-unflag-threads"></a>Para quitar marcadores de subprocesos

Para quitar marcadores de subprocesos, haga clic en uno o más subprocesos marcados en el **inspección paralela** ventana y elija **Quitar marcador**.

## <a name="bkmk_freeze"></a> Inmovilizar y reanudar la ejecución de subprocesos 

> [!TIP]
> Puede inmovilizar y descongelar (suspender y reanudar) los subprocesos para controlar el orden en que subprocesos realizan el trabajo. Esto puede ayudarle a resolver problemas de simultaneidad, como interbloqueos y condiciones de carrera.
  
#### <a name="to-freeze-and-unfreeze-threads"></a>Para inmovilizar y descongelar subprocesos  
  
1.  En el **inspección paralela** ventana, con todas las filas seleccionadas, secundario y seleccione **inmovilizar**.

    En la segunda columna, aparece ahora un icono de pausa para cada fila. El icono de pausa indica que el subproceso está inmovilizado.

2.  Anule la selección de las filas, haga clic en una sola fila.

3.  Haga clic en una fila y seleccione **reanudar**.

    Desaparece el icono de pausa en esta fila, que indica que el subproceso ya no está inmovilizado.

4.  Cambie al editor de código y haga clic en **F11**. Se ejecuta solo el subproceso no está inmovilizado.

    La aplicación también puede crear instancias de algunos nuevos subprocesos. Tenga en cuenta que todos los nuevos subprocesos sin marcar y no están inmovilizados.

## <a name="bkmk_follow_a_thread"></a> Siga un solo subproceso mediante el uso de puntos de interrupción condicionales

En ocasiones, puede ser útil comprobar la ejecución de un único subproceso en el depurador. Puede hacerlo de una forma es inmovilizar subprocesos que no está interesado en, pero en algunos escenarios puede que desee seguir un único subproceso, sin inmovilizar otros subprocesos (para la reproducción de un determinado de errores, por ejemplo). Para seguir un subproceso sin inmovilizar otros subprocesos, debe evitar interrumpir el código, excepto en el subproceso que le interesen. Puede hacerlo estableciendo un [punto de interrupción condicional](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).

Puede establecer puntos de interrupción en distintas condiciones, como el nombre del subproceso o el identificador de subproceso. Otro método que puede resultar útil es establecer la condición en los datos que se sabe que será único para cada subproceso. Se trata de un escenario de depuración comunes, en el que está más interesado en algún valor de datos concreto que en cualquier subproceso en particular.

#### <a name="to-follow-a-single-thread"></a>Seguir un único subproceso

1. Haga clic en el punto de interrupción creado previamente y elija **condiciones**.

2. En el **configuración de punto de interrupción** ventana, escriba `data == 5` para la expresión condicional.

    ![Punto de interrupción condicional](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

    > [!TIP]
    > Si está más interesado en un subproceso concreto, utilice un nombre de subproceso o el Id. de subproceso para la condición. Para hacer esto en el **configuración de punto de interrupción** ventana, seleccione **filtro** en lugar de **expresión condicional**y siga las sugerencias de filtro. Es posible que desee entre los subprocesos en código de la aplicación (ya que los identificadores de subprocesos cambia al reiniciar el depurador).

3. Cerrar la **configuración de punto de interrupción** ventana.

4. Haga clic en el reinicio ![Reiniciar aplicación](../debugger/media/dbg-tour-restart.png "RestartApp") botón reiniciar la sesión de depuración.

    Se interrumpirá en el código en el subproceso para el que la variable de datos es 5. Busque la flecha amarilla (contexto actual del depurador) el **inspección paralela** ventana para comprobar que.

5. Ahora, puede recorrer el código (F10) y entrar en el código (F11) y seguir la ejecución de subproceso único.

    Siempre que es única para el subproceso de la condición de punto de interrupción y el depurador no alcanza a cualquier otro punto de interrupción en otros subprocesos (es posible que deba deshabilitarlas), puede ir al código sin tener que cambiar a otros subprocesos y recorrer el código.

    > [!NOTE]
    > Al avanzar el depurador, se ejecutarán todos los subprocesos. Sin embargo, el depurador no interrumpe el código en otros subprocesos a menos que uno de los demás subprocesos alcanza un punto de interrupción. 
  
## <a name="more-about-the-multithreaded-debugging-windows"></a>Más información acerca de las ventanas de depuración multiproceso 

#### <a name="to-switch-to-another-thread"></a>Para cambiar a otro subproceso 

- Para cambiar a otro subproceso, vea [Cómo: cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md) 

#### <a name="to-learn-more-about-the-parallel-stack-and-parallel-watch-windows"></a>Para obtener más información sobre las ventanas pila paralelas y la inspección paralela  
  
- Vea [Cómo: utilizar la ventana Pila de paralelos](../debugger/using-the-parallel-stacks-window.md) 

- Vea [Cómo: utilizar la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md) 
  
## <a name="see-also"></a>Vea también  
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Cómo: Cambiar a otro subproceso durante la depuración](../debugger/how-to-switch-to-another-thread-while-debugging.md)
