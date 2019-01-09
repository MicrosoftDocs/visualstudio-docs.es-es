---
title: Análisis de datos de uso de CPU (ASP.NET)
description: Medición del rendimiento de aplicación en aplicaciones ASP.NET con la herramienta de diagnóstico de uso de CPU
ms.custom: mvc
ms.date: 08/06/2018
ms.topic: quickstart
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 594c6660c306faef635d14f60f1d717a04678db5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837399"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-aspnet"></a>Inicio rápido: Analizar datos de uso de la CPU en Visual Studio (ASP.NET)

Visual Studio proporciona muchas características eficaces para ayudar a analizar problemas de rendimiento de la aplicación. En este tema se proporciona una forma rápida de obtener información sobre las características básicas. A continuación, veremos una herramienta para identificar los cuellos de botella de rendimiento debido al uso elevado de la CPU. Se admiten las herramientas de diagnóstico para el desarrollo de .NET en Visual Studio, incluido ASP.NET, y para el desarrollo nativo de C++.

El concentrador de diagnósticos le ofrece muchas otras opciones para ejecutar y administrar la sesión de diagnóstico. Si la herramienta **Uso de CPU** que se describe aquí no proporciona los datos que necesita, las [demás herramientas de generación de perfiles](../profiling/profiling-feature-tour.md) proporcionan diferentes tipos de información que pueden resultarle útiles. En muchos casos, el cuello de botella de rendimiento de la aplicación puede no ser debido a la CPU, sino a la memoria, la representación de interfaz de usuario o el tiempo de solicitud de red.

Para ejecutar las herramientas de generación de perfiles con el depurador se requiere Windows 8 y versiones posteriores (ventana **Herramientas de diagnóstico**). En Windows 7 y versiones posteriores, puede usar la herramienta de análisis post mortem [Performance Profiler](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Crear un proyecto

1. En Visual Studio, seleccione **Archivo** > **Nuevo proyecto**.

1. En **Visual C#**, seleccione **Web** y, después, en el panel central, seleccione **Aplicación web ASP.NET (.NET Framework)**.

    Si no ve la plantilla de proyecto **Aplicación web de ASP.NET**, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de ASP.NET y web** y después elija **Modificar**.

1. Escriba un nombre como **MyProfilingApp_MVC** y haga clic en **Aceptar**.

1. En el cuadro de diálogo que aparece, seleccione **MVC** en el panel central y, después, haga clic en **Aceptar**.

    Visual Studio crea el proyecto. En el Explorador de soluciones (el panel de la derecha) se muestran los archivos de proyecto.

1. En el Explorador de soluciones, haga clic con el botón derecho en la carpeta de modelos y elija **Agregar** > **Clase**.

1. Asigne el nombre `Data.cs` a la nueva clase y haga clic en **Agregar**.

1. En el Explorador de soluciones, abra `Models/Data.cs` y agregue la siguiente instrucción `using` a la parte superior del archivo:

    ```csharp
    using System.Threading;
    ```

1. En Data.cs, reemplace el código siguiente:

    ```csharp
    public class Data
    {
    }
    ```

    con este código:

    ```csharp
    public class ServerClass
    {
        const int MIN_ITERATIONS = int.MaxValue / 1000;
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

        long m_totalIterations = 0;
        readonly object m_totalItersLock = new object();
        // The method that will be called when the thread is started.
        public void GenerateData()
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
        int numberOfThreads = 200;

        public Simple()
        {
            for (int i = 0; i < numberOfThreads; i++)
            {
                CreateThreads();
            }
        }
        public static void CreateThreads()
        {
            ServerClass serverObject = new ServerClass();

            Thread InstanceCaller = new Thread(new ThreadStart(serverObject.GenerateData));
            // Start the thread.
            InstanceCaller.Start();

            Console.WriteLine("The Main() thread calls this after "
                + "starting the new InstanceCaller thread.");

        }

        public int GetData()
        {
            // Not returning any meaningful data.
            return numberOfThreads;
        }
    }
    ```

1. En el Explorador de soluciones, abra *Controller/HomeControllers.cs* y reemplace el código siguiente:

    ```csharp
    public ActionResult About()
    {
        ViewBag.Message = "Your application description page.";

        return View();
    }
    ```

    con este código:

    ```csharp
    public ActionResult About()
    {
        Models.Simple s = new Models.Simple();

        ViewBag.Message = "Your application description page.";

        return View(s.GetData());
    }
    ```

##  <a name="step-1-collect-profiling-data"></a>Paso 1: Recopilar datos de generación de perfiles 
  
1.  En primer lugar, establezca un punto de interrupción en la aplicación en esta línea de código en el constructor `Simple`:

    `for (int i = 0; i < 200; i++)`

    Para establecer un punto de interrupción, haga clic en el margen interno a la izquierda de la línea de código.

1.  Después, establezca un segundo punto de interrupción en la llave de cierre al final del constructor `Simple`:

     ![Establecer puntos de interrupción para la generación de perfiles](../profiling/media/quickstart-cpu-usage-breakpoints-aspnet.png)

    > [!TIP]
    > Al establecer dos puntos de interrupción, puede limitar la recopilación de datos a las partes del código que quiere analizar.
  
1.  La ventana **Herramientas de diagnóstico** ya es visible, a menos que se haya desactivado. Para que la ventana se vuelva a mostrar, haga clic en **Depurar** > **Windows** > **Mostrar Herramientas de diagnóstico**.

1.  Haga clic en **Depurar** > **Iniciar depuración** (o en **Inicio** en la barra de herramientas, o presione **F5**).

1.  Cuando la aplicación termine de cargarse, haga clic en el vínculo **Acerca de** en la parte superior de la página web para empezar a ejecutar el código nuevo.

1.  Mire la vista **Resumen** de las Herramientas de diagnóstico que aparece.

1.  Mientras el depurador está en pausa, habilite la recopilación de datos de uso de la CPU mediante la selección de **Registrar perfil CPU** y, después, abra la pestaña **Uso de CPU**.

     ![Herramientas de diagnóstico para habilitar la generación de perfiles de CPU](../profiling/media/quickstart-cpu-usage-summary.png)

     Cuando se habilita la recopilación de datos, el botón de grabación muestra un círculo rojo.

     Al seleccionar **Registrar perfil CPU**, Visual Studio iniciará la grabación de las funciones y cuánto tiempo se tardan en ejecutar, y también proporciona un gráfico de escala de tiempo que se puede usar para centrarse en segmentos específicos de la sesión de muestreo. Estos datos recopilados solo se pueden ver cuando la aplicación se detiene en un punto de interrupción.

6.  Presione F5 para ejecutar la aplicación hasta el segundo punto de interrupción.

     Ahora tiene los datos de rendimiento de la aplicación específicamente para la región de código que se ejecuta entre los dos puntos de interrupción.

     El generador de perfiles empieza a preparar los datos de subproceso. Espere a que finalice.
  
     La herramienta Uso de CPU muestra el informe en la pestaña **Uso de CPU**.

     En este punto, puede empezar a analizar los datos.

## <a name="step-2-analyze-cpu-usage-data"></a>Paso 2: Analizar datos de uso de CPU

Se recomienda que, para empezar a analizar los datos, examine la lista de funciones de Uso de CPU, identifique las funciones que realizan la mayor parte del trabajo y, a continuación, observe detenidamente cada una de ellas.

1. En la lista de funciones, examine las funciones que realizan la mayor parte del trabajo.

     ![Pestaña Uso de CPU de herramientas de diagnóstico](../profiling/media/quickstart-cpu-usage-cpu-aspnet.png)

    > [!TIP]
    > Las funciones aparecen en orden, comenzando por las que realizan la mayor parte del trabajo (no están en orden de llamada). Esto ayuda a identificar rápidamente las funciones que se ejecutan durante más tiempo.

2. En la lista de funciones, haga doble clic en la función `MyProfilingApp_MVC.Models.ServerClass::GetNumber`.

    Al hacer doble clic en la función, se abre la vista **Llamador y destinatario** en el panel de la izquierda. 

    ![Vista Llamador de herramientas de diagnóstico](../profiling/media/quickstart-cpu-usage-caller-callee-aspnet.png)

    En esta vista, la función seleccionada se muestra en el título y en el cuadro **Función actual** (en este ejemplo, `ServerClass::GetNumber`). La función que llamó a la función actual se muestra a la izquierda en **Función llamadora**, y las funciones llamadas por la función actual se muestran a la derecha en el cuadro **Funciones llamadas**. (Puede seleccionar cualquiera de los cuadros para cambiar la función actual).

    En esta vista se muestra el tiempo total (ms) y el porcentaje del tiempo de ejecución global de la aplicación que la función ha tardado en completarlo.

    **Cuerpo de la función** también muestra la cantidad total de tiempo (y el porcentaje de tiempo) empleado en el cuerpo de la función, excluido el tiempo invertido en las funciones llamadoras y llamadas. (En este ejemplo, 2220 de 2235 ms se dedicaron al cuerpo de la función y el tiempo restante (<20 ms) se dedicó al código externo al que esta función llama). Los valores reales serán diferentes en función del entorno.

    > [!TIP]
    > Los valores altos en **Cuerpo de la función** pueden indicar un cuello de botella de rendimiento dentro de la propia función.

## <a name="next-steps"></a>Pasos siguientes

- [Analizar el uso de memoria](../profiling/memory-usage.md) para identificar los cuellos de botella de rendimiento.
- [Analizar el uso de la CPU](../profiling/cpu-usage.md) para obtener información más detallada sobre la herramienta de uso de CPU.
- Analizar el uso de la CPU sin un depurador adjunto o tomando una aplicación en ejecución como destino. Para más información, vea [Recopilar datos de generación de perfiles sin depurar](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) en [Ejecutar herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Vea también  

 [Generación de perfiles en Visual Studio](../profiling/index.md)  
 [Primer vistazo a la generación de perfiles](../profiling/profiling-feature-tour.md)
