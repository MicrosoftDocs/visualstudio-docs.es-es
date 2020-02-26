---
title: Análisis de los datos de uso de CPU (C#, Visual Basic)
description: Medición del rendimiento de aplicación en C# y Visual Basic con la herramienta de diagnóstico de uso de CPU
ms.custom: mvc
ms.date: 02/14/2020
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8fd77fe5fc00e8c1a3b487c93a6004b2f8cf7060
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558199"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c-visual-basic"></a>Inicio rápido: Análisis de los datos de uso de CPU en Visual Studio (C#, Visual Basic)

Visual Studio proporciona muchas características eficaces para ayudar a analizar problemas de rendimiento de la aplicación. En este tema se proporciona una forma rápida de obtener información sobre las características básicas. A continuación, veremos la herramienta para identificar los cuellos de botella de rendimiento debido al uso elevado de la CPU. Se admiten las herramientas de diagnóstico para el desarrollo de .NET en Visual Studio, incluido ASP.NET, y para el desarrollo nativo de C++.

El concentrador de diagnósticos le ofrece muchas otras opciones para ejecutar y administrar la sesión de diagnóstico. Si la herramienta **Uso de CPU** que se describe aquí no proporciona los datos que necesita, las [demás herramientas de generación de perfiles](../profiling/profiling-feature-tour.md) proporcionan diferentes tipos de información que pueden resultarle útiles. En muchos casos, el cuello de botella de rendimiento de la aplicación puede no ser debido a la CPU, sino a la memoria, la representación de interfaz de usuario o el tiempo de solicitud de red. El concentrador de diagnósticos le ofrece muchas más opciones para registrar y analizar este tipo de datos.

Para ejecutar las herramientas de generación de perfiles con el depurador se requiere Windows 8 y versiones posteriores (ventana **Herramientas de diagnóstico**). En Windows 7 y versiones posteriores, puede usar la herramienta de análisis post mortem [Performance Profiler](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Crear un proyecto

1. Abra Visual Studio y cree el proyecto.

   ::: moniker range="vs-2017"
   En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**.

   En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **C#** o **Visual Basic** y seleccione **.NET Core**. En el panel central, elija **Aplicación de consola (.NET Core)** . Después asigne al proyecto el nombre *MyProfilerApp*.

   Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)** , elija en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.
   ::: moniker-end
   ::: moniker range="vs-2019"
   Si la ventana de inicio no está abierta, elija **Archivo** > **Ventana Inicio**.

   En la ventana de inicio, elija **Crear un proyecto nuevo**.

   En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *consola*. Seguidamente, elija **C#** o **Visual Basic** en la lista de lenguajes y, luego, **Windows** en la lista de plataformas.

   Después de aplicar los filtros de lenguaje y plataforma, elija la plantilla **Aplicación de consola (.NET Core)** y luego, **Siguiente**.

   > [!NOTE]
   > Si no ve la plantilla **Aplicación de consola (.NET Core)** , puede instalarla desde la ventana **Crear un proyecto**. En el mensaje **¿No encuentra lo que busca?** , elija el vínculo **Instalar más herramientas y características**. Luego, en el Instalador de Visual Studio, elija la carga de trabajo **Desarrollo multiplataforma de .NET Core**.

   En la ventana **Configurar el nuevo proyecto**, escriba *MyProfilerApp* en el cuadro **Nombre del proyecto**. Luego, elija **Crear**.

   ::: moniker-end

   Visual Studio se abre en el nuevo proyecto.

2. Abra *Program.cs* y reemplace todo el código por el código siguiente:

    ```csharp
    using System;
    using System.Threading;
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void DoWork()
        {
            Console.WriteLine(
                "ServerClass.InstanceMethod is running on another thread.");

            var x = GetNumber();
        }

        private int GetNumber()
        {
            var rand = new Random();
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);
            var result = 0;
            lock (m_totalItersLock)
            {
                m_totalIterations += iters;
            }
            // we're just spinning here
            // and using Random to frustrate compiler optimizations
            for (var i = 0; i < iters; i++)
            {
                result = rand.Next();
            }
            return result;
        }
    }

    public class Simple
    {
        public static void Main()
        {
            for (int i = 0; i < 200; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.DoWork));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }
    }
    ```

    ```vb
    Imports System
    Imports System.Threading

    Namespace MyProfilerApp
        Public Class ServerClass
            Const MIN_ITERATIONS As Integer = Integer.MaxValue / 1000
            Const MAX_ITERATIONS As Integer = MIN_ITERATIONS + 10000

            Private m_totalIterations As Long = 0
            ReadOnly m_totalItersLock As New Object()
            ' The method that will be called when the thread is started.
            Public Sub DoWork()
                Console.WriteLine("ServerClass.InstanceMethod is running on another thread.")

                Dim x = GetNumber()
            End Sub

            Private Function GetNumber() As Integer
                Dim rand = New Random()
                Dim iters = rand.[Next](MIN_ITERATIONS, MAX_ITERATIONS)
                Dim result = 0
                SyncLock m_totalItersLock
                    m_totalIterations += iters
                End SyncLock
                ' we're just spinning here
                ' and using Random to frustrate compiler optimizations
                For i As Integer = 0 To iters - 1
                    result = rand.[Next]()
                Next
                Return result
            End Function
        End Class

        Public Class Simple
            Public Shared Sub Main()
                For i As Integer = 0 To 199
                    CreateThreads()
                Next
            End Sub
            Public Shared Sub CreateThreads()
                Dim serverObject As New ServerClass()

                Dim InstanceCaller As New Thread(New ThreadStart(AddressOf serverObject.DoWork))
                ' Start the thread.
                InstanceCaller.Start()

                Console.WriteLine("The Main() thread calls this after " + "starting the new InstanceCaller thread.")

            End Sub
        End Class
    End Namespace
    ```

    > [!NOTE]
    > En Visual Basic, asegúrese de que el objeto de inicio se establece en `Sub Main` (**Propiedades** > **Aplicaciones** > **Objeto de inicio**).

## <a name="step-1-collect-profiling-data"></a>Paso 1: Recopilar datos de generación de perfiles

1. En primer lugar, establezca un punto de interrupción en la aplicación en esta línea de código en la función `Main`:

    `for (int i = 0; i < 200; i++)`

    o bien, para Visual Basic:

    `For i As Integer = 0 To 199`

    Para establecer un punto de interrupción, haga clic en el margen interno a la izquierda de la línea de código.

2. Después, establezca un segundo punto de interrupción en la llave de cierre al final de la función `Main`:

     ![Establecimiento de puntos de interrupción para la generación de perfiles](../profiling/media/quickstart-cpu-usage-breakpoints.png "Establecer puntos de interrupción para la generación de perfiles")

    > [!TIP]
    > Al establecer dos puntos de interrupción, puede limitar la recopilación de datos a las partes del código que quiere analizar.

3. La ventana **Herramientas de diagnóstico** ya es visible, a menos que se haya desactivado. Para que la ventana se vuelva a mostrar, haga clic en **Depurar** > **Windows** > **Mostrar Herramientas de diagnóstico**.

4. Haga clic en **Depurar** > **Iniciar depuración** (o en **Inicio** en la barra de herramientas, o presione **F5**).

     Cuando la aplicación termine de cargarse, se muestra la vista **Resumen** de las Herramientas de diagnóstico.

5. Mientras el depurador está en pausa, habilite la recopilación de datos de uso de la CPU mediante la selección de **Registrar perfil CPU** y, después, abra la pestaña **Uso de CPU**.

     ![Herramientas de diagnóstico para habilitar la generación de perfiles de CPU](../profiling/media/quickstart-cpu-usage-summary.png "Herramientas de diagnóstico para habilitar la generación de perfiles de CPU")

     Cuando se habilita la recopilación de datos, el botón de grabación muestra un círculo rojo.

     Al seleccionar **Registrar perfil CPU**, Visual Studio iniciará la grabación de las funciones y cuánto tiempo se tardan en ejecutar, y también proporciona un gráfico de escala de tiempo que se puede usar para centrarse en segmentos específicos de la sesión de muestreo. Estos datos recopilados solo se pueden ver cuando la aplicación se detiene en un punto de interrupción.

6. Presione **F5** para ejecutar la aplicación hasta el segundo punto de interrupción.

     Ahora tiene los datos de rendimiento de la aplicación específicamente para la región de código que se ejecuta entre los dos puntos de interrupción.

     El generador de perfiles empieza a preparar los datos de subproceso. Espere a que finalice.

     La herramienta Uso de CPU muestra el informe en la pestaña **Uso de CPU**.

     En este punto, puede empezar a analizar los datos.

## <a name="step-2-analyze-cpu-usage-data"></a>Paso 2: Analizar datos de uso de CPU

Se recomienda que, para empezar a analizar los datos, examine la lista de funciones de Uso de CPU, identifique las funciones que realizan la mayor parte del trabajo y, a continuación, observe detenidamente cada una de ellas.

1. En la lista de funciones, examine las funciones que realizan la mayor parte del trabajo.

     ![Pestaña Uso de CPU de herramientas de diagnóstico](../profiling/media/quickstart-cpu-usage-cpu.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Las funciones aparecen en orden, comenzando por las que realizan la mayor parte del trabajo (no están en orden de llamada). Esto ayuda a identificar rápidamente las funciones que se ejecutan durante más tiempo.

2. En la lista de funciones, haga doble clic en la función `ServerClass::GetNumber`.

    Al hacer doble clic en la función, se abre la vista **Llamador y destinatario** en el panel de la izquierda.

    ![Vista Llamador de herramientas de diagnóstico](../profiling/media/quickstart-cpu-usage-caller-callee.png "DiagToolsCallerCallee")

    En esta vista, la función seleccionada se muestra en el título y en el cuadro **Función actual** (en este ejemplo, `GetNumber`). La función que llamó a la función actual se muestra a la izquierda en **Función llamadora**, y las funciones llamadas por la función actual se muestran a la derecha en el cuadro **Funciones llamadas**. (Puede seleccionar cualquiera de los cuadros para cambiar la función actual).

    En esta vista se muestra el tiempo total (ms) y el porcentaje del tiempo de ejecución global de la aplicación que la función ha tardado en completarlo.

    **Cuerpo de la función** también muestra la cantidad total de tiempo (y el porcentaje de tiempo) empleado en el cuerpo de la función, excluido el tiempo invertido en las funciones llamadoras y llamadas. (En esta ilustración, 2856 de 2863 ms se dedicaron al cuerpo de la función y el tiempo restante (<20 ms) se dedicó al código externo al que esta función llama). Los valores reales serán diferentes en función del entorno.

    > [!TIP]
    > Los valores altos en **Cuerpo de la función** pueden indicar un cuello de botella de rendimiento dentro de la propia función.

## <a name="next-steps"></a>Pasos siguientes

- [Analizar el uso de memoria](../profiling/memory-usage.md) para identificar los cuellos de botella de rendimiento.
- [Analizar el uso de la CPU](../profiling/cpu-usage.md) para obtener información más detallada sobre la herramienta de uso de CPU.
- Analizar el uso de la CPU sin un depurador adjunto o tomando una aplicación en ejecución como destino. Para más información, vea [Recopilar datos de generación de perfiles sin depurar](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) en [Ejecutar herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Vea también

- [Generación de perfiles en Visual Studio](../profiling/index.yml)
- [Primer vistazo a la generación de perfiles](../profiling/profiling-feature-tour.md)
