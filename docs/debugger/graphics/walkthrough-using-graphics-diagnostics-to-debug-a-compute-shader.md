---
title: Depuración de un sombreador de cálculo mediante diagnóstico de gráficos
description: Vea un ejemplo de solución de problemas de un sombreador de cálculo. Verá el uso de Lista de eventos gráficos, Pila de llamadas de eventos gráficos y Etapas de canalización de gráficos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 184e009c870e6a15ce61ed14dcb8b6916e293728
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908516"
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>Tutorial: Uso de Diagnóstico de gráficos para depurar un sombreador de cálculo
En este tutorial se muestra cómo usar las herramientas de diagnóstico de gráficos de Visual Studio para investigar un sombreador de cálculo que genera resultados incorrectos.

 En el tutorial se muestran las tareas siguientes:

- Uso de la **Lista de eventos gráficos** para buscar los posibles orígenes del problema.

- Uso de la **Pila de llamadas de eventos gráficos** para determinar qué sombreador de cálculo se ejecuta mediante un evento `Dispatch` de DirectCompute.

- Uso de la ventana **Etapas de canalización de gráficos** y del depurador HSLS para examinar el sombreador de cálculo en el que se origina el problema.

## <a name="scenario"></a>Escenario
 En este escenario se ha escrito una simulación de dinámica de fluidos en la que se usa DirectCompute para realizar el trabajo de cálculo más intensivo en la actualización de la simulación. Cuando se ejecuta la aplicación, la representación del conjunto de datos y de la interfaz de usuario parece correcta, pero la simulación no se comporta de la manera esperada. Con el diagnóstico de gráficos puede capturar el problema en un registro de gráficos de modo que pueda depurar la aplicación. El problema tiene este aspecto en la aplicación:

 ![El fluido simulado se comporta de forma incorrecta.](media/gfx_diag_demo_compute_shader_fluid_problem.png "gfx_diag_demo_compute_shader_fluid_problem")

 Para obtener información sobre cómo capturar los problemas de gráficos en un registro de gráficos, vea [Capturing Graphics Information](capturing-graphics-information.md).

## <a name="investigation"></a>Investigación
 Use las herramientas de diagnóstico de gráficos para cargar el archivo de registro de gráficos que le permitirá inspeccionar los fotogramas capturados.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar un fotograma en un registro de gráficos

1. En Visual Studio, cargue un registro de gráficos que contenga un fotograma en el que se muestren resultados incorrectos de la simulación. En Visual Studio aparece una nueva pestaña de diagnóstico de gráficos. En la parte superior de esta pestaña está la salida del destino de representación del fotograma seleccionado. En la parte inferior está la **Lista de fotogramas** con una miniatura de los fotogramas capturados.

2. En la **Lista de fotogramas**, seleccione un fotograma que muestre el comportamiento incorrecto de la simulación. Aunque parezca que el error se encuentra en el código de simulación y no en el de representación, tendrá que elegir un fotograma, ya que los eventos de DirectCompute se capturan por fotogramas junto con los eventos de Direct3D. En este escenario, la pestaña de registro de gráficos tiene el aspecto siguiente:

    ![Documento de registro de gráficos en Visual Studio.](media/gfx_diag_demo_compute_shader_fluid_step_1.png "gfx_diag_demo_compute_shader_fluid_step_1")

   Después de seleccionar un fotograma en el que se muestre el problema, puede usar la **Lista de eventos gráficos** para diagnosticarlo. La **Lista de eventos gráficos** contiene un evento para las llamadas de DirectCompute y las llamadas API de Direct3D que se realizaron durante el fotograma activo; por ejemplo, llamadas API para ejecutar un cálculo en la GPU o para representar el conjunto de datos o la interfaz de usuario. En este caso, nos interesan los eventos `Dispatch` que representan elementos de la simulación que se ejecutan en la GPU.

#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>Para buscar el evento Dispatch de la actualización de simulación

1. En la barra de herramientas del **Diagnóstico de gráficos**, elija **Lista de eventos** para abrir la ventana **Lista de eventos gráficos**.

2. Inspeccione la **Lista de eventos gráficos** y busque el evento de dibujo (Draw) que representa el conjunto de datos. Para facilitar esta tarea, escriba `Draw` en el cuadro **Búsqueda** de la esquina superior derecha de la ventana **Lista de eventos gráficos**. Con esto se filtra la lista para que solo incluya los eventos que tienen la palabra “Draw” en sus títulos. En este escenario, verá que se produjeron los siguientes eventos de dibujo:

    ![La lista de eventos muestra eventos Draw.](media/gfx_diag_demo_compute_shader_fluid_step_2.png "gfx_diag_demo_compute_shader_fluid_step_2")

3. Desplácese por cada evento de dibujo mientras observa el destino de representación en la pestaña del documento de registro de gráficos.

4. Deténgase cuando el destino de representación muestre por primera vez el conjunto de datos representado. En este escenario, el conjunto de datos se representa en el primer evento de dibujo. Se muestra el error de la simulación:

    ![Este evento Draw presenta el conjunto de datos de simulación.](media/gfx_diag_demo_compute_shader_fluid_step_3.png "gfx_diag_demo_compute_shader_fluid_step_3")

5. Ahora inspeccione la **Lista de eventos gráficos** y busque el evento `Dispatch` que actualiza la simulación. Dado que es probable que la simulación se actualice antes de representarse, puede concentrarse primero en los eventos `Dispatch` que ocurren antes del evento de dibujo que representa los resultados. Para facilitar esta tarea, modifique el cuadro **Búsqueda** para que muestre `Draw;Dispatch;CSSetShader(`. De este modo, la lista se filtra para que también contenga los eventos `Dispatch` y `CSSetShader`, además de los eventos de dibujo. En este escenario, verá que se produjeron varios eventos `Dispatch` antes que el evento de dibujo:

    ![La lista de eventos muestra eventos Draw, Dispatch y CSSetShader](media/gfx_diag_demo_compute_shader_fluid_step_4.png "gfx_diag_demo_compute_shader_fluid_step_4")

   Ahora que ya sabe cuáles son los eventos `Dispatch` que podrían corresponderse con el problema, puede examinarlos con más detalle.

#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Para determinar qué sombreador de cálculo se ejecuta con una llamada Dispatch

1. En la barra de herramientas del **Diagnóstico de gráficos**, elija **Pila de llamadas de eventos** para abrir la ventana **Lista de eventos gráficos**.

2. Comenzando desde el evento de dibujo que representa los resultados de la simulación, desplácese hacia atrás por cada evento `CSSetShader` anterior. Luego, en la ventana **Pila de llamadas de eventos de gráficos**, elija la función de nivel superior para navegar al sitio de llamada. En el sitio de llamada, puede usar el primer parámetro de la llamada de función [CSSetShader](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-cssetshader) para determinar qué sombreador de cálculo se ejecutará con el siguiente evento `Dispatch`.

   En este escenario, hay tres pares de eventos `CSSetShader` y `Dispatch` en cada fotograma. Comenzando desde atrás, el tercer par representa el paso de integración (donde las partículas fluidas se mueven realmente), el segundo par representa el paso de cálculo de fuerza (donde se calculan las fuerzas que afectan a cada partícula) y el primer par representa el paso de cálculo de densidad.

#### <a name="to-debug-the-compute-shader"></a>Para depurar al sombreador de cálculo

1. En la barra de herramientas del **Diagnóstico de gráficos**, elija **Etapas de canalización** para abrir la ventana **Etapas de canalización de gráficos**.

2. Seleccione el tercer evento `Dispatch` (el que precede inmediatamente al evento de dibujo) y después en la ventana **Etapas de canalización de gráficos**, en la etapa **Sombreador de cálculo**, elija **Iniciar depuración**.

    ![Selección del tercer evento Dispatch en la lista de eventos.](media/gfx_diag_demo_compute_shader_fluid_step_6.png "gfx_diag_demo_compute_shader_fluid_step_6")

    El depurador de HLSL se inicia en el sombreador que realiza el paso de la integración.

3. Examine el código fuente del sombreador de cálculo en el paso de integración y busque el origen del error. Cuando use el diagnóstico de gráficos para depurar el código del sombreador de cálculo de HLSL, puede ejecutar el código paso a paso y usar otras herramientas de depuración conocidas como las ventanas Inspección. En este escenario, no parece que haya un error en el sombreador de cálculo que realiza el paso de integración.

    ![Depuración del sombreador de cálculo IntegrateCS.](media/gfx_diag_demo_compute_shader_fluid_step_7.png "gfx_diag_demo_compute_shader_fluid_step_7")

4. Para detener la depuración del sombreador de cálculo, en la barra de herramientas **Depurar**, elija **Detener depuración** (teclado: Mayús+F5).

5. A continuación, seleccione el segundo evento `Dispatch` e inicie la depuración del sombreador de cálculo tal y como hizo en el paso anterior.

    ![Selección del segundo evento Dispatch en la lista de eventos.](media/gfx_diag_demo_compute_shader_fluid_step_8.png "gfx_diag_demo_compute_shader_fluid_step_8")

    El depurador de HLSL se inicia en el sombreador que calcula las fuerzas que actúan sobre cada partícula de fluido.

6. Examine el código fuente del sombreador de cálculo en el paso de cálculo de fuerza. En este caso, se determina que aquí está el origen del error.

    ![Depuración del sombreador de cálculo ForceCS_Simple.](media/gfx_diag_demo_compute_shader_fluid_step_9.png "gfx_diag_demo_compute_shader_fluid_step_9")

   Después de determinar la ubicación del error, puede detener la depuración y modificar el código fuente de sombreador de cálculo para calcular correctamente la distancia entre las partículas interactivas. En este escenario, simplemente se cambia la línea de `float2 diff = N_position + P_position;` a `float2 diff = N_position - P_position;`:

   ![Código del sombreador de cálculo corregido.](media/gfx_diag_demo_compute_shader_fluid_step_10.png "gfx_diag_demo_compute_shader_fluid_step_10")

   En este escenario, dado que los sombreadores de cálculo se compilan en tiempo de ejecución, reinicie la aplicación después de realizar los cambios para observar cómo afectan a la simulación. No es necesario que vuelva a compilar la aplicación. Cuando ejecute la aplicación, verá que la simulación se comporta ahora correctamente.

   ![El fluido simulado se comporta de forma correcta.](media/gfx_diag_demo_compute_shader_fluid_resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")