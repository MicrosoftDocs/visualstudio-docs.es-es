---
title: Análisis de datos de uso de CPU (C++)
description: Medición del rendimiento de aplicación en C++ con la herramienta de diagnóstico de uso de CPU
ms.date: 08/06/2018
ms.topic: quickstart
f1_keywords:
- ''
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 2f2587d621715e6e04edade779116e22d021072c
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128181"
---
# <a name="quickstart-analyze-cpu-usage-data-in-visual-studio-c"></a>Inicio rápido: Analizar datos de uso de CPU en Visual Studio (C++)

Visual Studio proporciona muchas características eficaces para ayudarle a analizar problemas de rendimiento de la aplicación. En este tema se proporciona una forma rápida de obtener información sobre las características básicas. A continuación, veremos la herramienta para identificar los cuellos de botella de rendimiento debido al uso elevado de la CPU. Se admiten las herramientas de diagnóstico para el desarrollo de .NET en Visual Studio, incluido ASP.NET, y para el desarrollo nativo de C++.

El concentrador de diagnósticos le ofrece muchas otras opciones para ejecutar y administrar la sesión de diagnóstico. Si la herramienta **Uso de CPU** que se describe aquí no proporciona los datos que necesita, las [demás herramientas de generación de perfiles](../profiling/profiling-feature-tour.md) proporcionan diferentes tipos de información que pueden resultarle útiles. En muchos casos, el cuello de botella de rendimiento de la aplicación puede no ser debido a la CPU, sino a la memoria, la representación de interfaz de usuario o el tiempo de solicitud de red. El concentrador de diagnósticos le ofrece muchas más opciones para registrar y analizar este tipo de datos.

Para ejecutar las herramientas de generación de perfiles con el depurador se requiere Windows 8 y versiones posteriores (ventana **Herramientas de diagnóstico**). En Windows 7 y versiones posteriores, puede usar la herramienta de análisis post mortem [Performance Profiler](../profiling/profiling-feature-tour.md).

## <a name="create-a-project"></a>Crear un proyecto

1. En Visual Studio, seleccione **Archivo** > **Nuevo proyecto**.

2. Bajo **Visual C++** , seleccione **Escritorio de Windows** y, después, elija **Aplicación de consola Windows** en el panel central.

    Si no ve la plantilla de proyecto **Aplicación de consola Windows**, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

3. Escriba un nombre como **Diagnostics_Get_Started_Native** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto.

4. En *MyDbgApp.cpp*, reemplace el código siguiente:

    ```c++
    int main()
    {
        return 0;
    }
    ```

    con este código (no quite `#include "stdafx.h"`):

    ```c++
    #include <iostream>
    #include <limits>
    #include <mutex>
    #include <random>
    #include <functional>

    //.cpp file code:

    static constexpr int MIN_ITERATIONS = std::numeric_limits<int>::max() / 1000;
    static constexpr int MAX_ITERATIONS = MIN_ITERATIONS + 10000;

    long long m_totalIterations = 0;
    std::mutex m_totalItersLock;

    int getNumber()
    {

        std::uniform_int_distribution<int> num_distribution(MIN_ITERATIONS, MAX_ITERATIONS);
        std::mt19937 random_number_engine; // pseudorandom number generator
        auto get_num = std::bind(num_distribution, random_number_engine);
        int random_num = get_num();

        auto result = 0;
        {
            std::lock_guard<std::mutex> lock(m_totalItersLock);
            m_totalIterations += random_num;
        }
        // we're just spinning here
        // to increase CPU usage
        for (int i = 0; i < random_num; i++)
        {
            result = get_num();
        }
        return result;
    }

    void doWork()
    {
        std::wcout << L"The doWork function is running on another thread." << std::endl;

        auto x = getNumber();
    }

    int main()
    {
        std::vector<std::thread> threads;

        for (int i = 0; i < 10; ++i) {

            threads.push_back(std::thread(doWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }

        for (auto& thread : threads) {
            thread.join();
        }

        return 0;
    }
    ```

## <a name="step-1-collect-profiling-data"></a>Paso 1: Recopilar datos de generación de perfiles

1. En primer lugar, establezca un punto de interrupción en la aplicación en esta línea de código en la función `main`:

    `for (int i = 0; i < 10; ++i) {`

    Para establecer un punto de interrupción, haga clic en el margen interno a la izquierda de la línea de código.

2. Después, establezca un segundo punto de interrupción en la llave de cierre al final de la función `main`:

     ![Establecer puntos de interrupción para la generación de perfiles](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Establecer puntos de interrupción para la generación de perfiles")

    > [!TIP]
    > Al establecer dos puntos de interrupción, puede limitar la recopilación de datos a las partes del código que quiere analizar.

3. La ventana **Herramientas de diagnóstico** ya es visible, a menos que se haya desactivado. Para que la ventana se vuelva a mostrar, haga clic en **Depurar** > **Windows** > **Mostrar Herramientas de diagnóstico**.

4. Haga clic en **Depurar** > **Iniciar depuración** (o en **Inicio** en la barra de herramientas, o presione **F5**).

     Cuando la aplicación termine de cargarse, se muestra la vista **Resumen** de las Herramientas de diagnóstico.

5. Mientras el depurador está en pausa, habilite la recopilación de datos de uso de la CPU mediante la selección de **Registrar perfil CPU** y, después, abra la pestaña **Uso de CPU**.

     ![Herramientas de diagnóstico para habilitar la generación de perfiles de CPU](../profiling/media/quickstart-cpu-usage-summary.png "Herramientas de diagnóstico para habilitar la generación de perfiles de CPU")

     Cuando se habilita la recopilación de datos, el botón de grabación muestra un círculo rojo.

     Al seleccionar **Registrar perfil CPU**, Visual Studio iniciará la grabación de las funciones y cuánto tiempo se tardan en ejecutar, y también proporciona un gráfico de escala de tiempo que se puede usar para centrarse en segmentos específicos de la sesión de muestreo. Estos datos recopilados solo se pueden ver cuando la aplicación se detiene en un punto de interrupción.

6. Presione F5 para ejecutar la aplicación hasta el segundo punto de interrupción.

     Ahora tiene los datos de rendimiento de la aplicación específicamente para la región de código que se ejecuta entre los dos puntos de interrupción.

     El generador de perfiles empieza a preparar los datos de subproceso. Espere a que finalice.

     La herramienta Uso de CPU muestra el informe en la pestaña **Uso de CPU**.

     En este punto, puede empezar a analizar los datos.

## <a name="step-2-analyze-cpu-usage-data"></a>Paso 2: Analizar datos de uso de CPU

Se recomienda que, para empezar a analizar los datos, examine la lista de funciones de Uso de CPU, identifique las funciones que realizan la mayor parte del trabajo y, a continuación, observe detenidamente cada una de ellas.

1. En la lista de funciones, examine las funciones que realizan la mayor parte del trabajo.

     ![Herramientas de diagnóstico para la pestaña Uso de CPU](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Las funciones aparecen en orden, comenzando por las que realizan la mayor parte del trabajo (no están en orden de llamada). Esto ayuda a identificar rápidamente las funciones que se ejecutan durante más tiempo.

2. En la lista de funciones, haga doble clic en la función `getNumber`.

    Al hacer doble clic en la función, se abre la vista **Llamador y destinatario** en el panel de la izquierda.

    ![Herramientas de diagnóstico para la vista Llamador y destinatario](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    En esta vista, la función seleccionada se muestra en el título y en el cuadro **Función actual** (en este ejemplo, `getNumber`). La función que llamó a la función actual se muestra a la izquierda en **Función llamadora**, y las funciones llamadas por la función actual se muestran a la derecha en el cuadro **Funciones llamadas**. (Puede seleccionar cualquiera de los cuadros para cambiar la función actual).

    En esta vista se muestra el tiempo total (ms) y el porcentaje del tiempo de ejecución global de la aplicación que la función ha tardado en completarlo.

    **Cuerpo de la función** también muestra la cantidad total de tiempo (y el porcentaje de tiempo) empleado en el cuerpo de la función, excluido el tiempo invertido en las funciones llamadoras y llamadas. (En esta ilustración, se dedicaron 119 de 43602 ms en el cuerpo de la función y el tiempo restante se invirtió en otro código llamado por esta función). Los valores reales serán muy diferentes en función del entorno.

    > [!TIP]
    > Los valores altos en **Cuerpo de la función** pueden indicar un cuello de botella de rendimiento dentro de la propia función.

## <a name="next-steps"></a>Pasos siguientes

- [Analizar el uso de memoria](../profiling/memory-usage.md) para identificar los cuellos de botella de rendimiento.
- [Analizar el uso de la CPU](../profiling/cpu-usage.md) para obtener información más detallada sobre la herramienta de uso de CPU.
- Analizar el uso de la CPU sin un depurador adjunto o tomando una aplicación en ejecución como destino. Para más información, vea [Recopilar datos de generación de perfiles sin depurar](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) en [Ejecutar herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Vea también

- [Generación de perfiles en Visual Studio](../profiling/index.yml)
- [Primer vistazo a la generación de perfiles](../profiling/profiling-feature-tour.md)
