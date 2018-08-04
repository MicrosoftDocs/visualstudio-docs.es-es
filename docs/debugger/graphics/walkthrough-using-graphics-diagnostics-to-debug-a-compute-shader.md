---
title: 'Tutorial: Usar diagnóstico de gráficos para depurar un sombreador de cálculo | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cff502344db59586709c350ad282871db9f587c8
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511845"
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>Tutorial: Usar diagnósticos de gráficos para depurar un sombreador de cálculo
En este tutorial se muestra cómo usar las herramientas de diagnóstico de gráficos de Visual Studio para investigar un sombreador de cálculo que genera resultados incorrectos.  
  
 En el tutorial se muestran las tareas siguientes:  
  
-   Uso de la **Lista de eventos gráficos** para buscar los posibles orígenes del problema.  
  
-   Mediante el **pila de llamadas de eventos de gráficos** para determinar qué cálculo sombreador es ejecutado por un DirectCompute `Dispatch` eventos.  
  
-   Mediante el **etapas de canalización de gráficos** ventana y HLSL del depurador para examinar el sombreador de cálculo que es el origen del problema.  
  
## <a name="scenario"></a>Escenario  
 En este escenario se ha escrito una simulación de dinámica de fluidos en la que se usa DirectCompute para realizar el trabajo de cálculo más intensivo en la actualización de la simulación. Cuando se ejecuta la aplicación, la representación del conjunto de datos y de la interfaz de usuario parece correcta, pero la simulación no se comporta de la manera esperada. Con el diagnóstico de gráficos puede capturar el problema en un registro de gráficos de modo que pueda depurar la aplicación. El problema tiene este aspecto en la aplicación:  
  
 ![El fluido simulado se comporta incorrectamente. ] (media/gfx_diag_demo_compute_shader_fluid_problem.png "gfx_diag_demo_compute_shader_fluid_problem")  
  
 Para obtener información sobre cómo capturar los problemas de gráficos en un registro de gráficos, vea [Capturing Graphics Information](capturing-graphics-information.md).  
  
## <a name="investigation"></a>Investigación  
 Use las herramientas de diagnóstico de gráficos para cargar el archivo de registro de gráficos que le permitirá inspeccionar los fotogramas capturados.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Para examinar un fotograma en un registro de gráficos  
  
1.  En Visual Studio, cargue un registro de gráficos que contenga un fotograma en el que se muestren resultados incorrectos de la simulación. En Visual Studio aparece una nueva pestaña de diagnóstico de gráficos. En la parte superior de esta pestaña está la salida del destino de representación del fotograma seleccionado. En la parte inferior es parte del **lista de fotogramas**, que muestra una vista en miniatura de cada fotograma capturado.  
  
2.  En el **lista de fotogramas**, seleccione un fotograma que muestre el comportamiento incorrecto de la simulación. Aunque parezca que el error se encuentra en el código de simulación y no en el de representación, tendrá que elegir un fotograma, ya que los eventos de DirectCompute se capturan por fotogramas junto con los eventos de Direct3D. En este escenario, la pestaña de registro de gráficos tiene el aspecto siguiente:  
  
     ![Documento de registro de gráficos en Visual Studio. ] (media/gfx_diag_demo_compute_shader_fluid_step_1.png "gfx_diag_demo_compute_shader_fluid_step_1")  
  
 Después de seleccionar un fotograma en el que se muestre el problema, puede usar la **Lista de eventos gráficos** para diagnosticarlo. El **lista de eventos gráficos** contiene un evento para cada llamada de DirectCompute y llamada a la API de Direct3D que se realizaron durante el fotograma activo; por ejemplo, llamadas de API para ejecutar un cálculo en la GPU o para representar el conjunto de datos o la interfaz de usuario. En este caso, nos interesan los eventos `Dispatch` que representan elementos de la simulación que se ejecutan en la GPU.  
  
#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>Para buscar el evento Dispatch de la actualización de simulación  
  
1.  En el **diagnóstico de gráficos** barra de herramientas, elija **lista de eventos** para abrir el **lista de eventos gráficos** ventana.  
  
2.  Inspeccionar el **lista de eventos gráficos** para el evento de dibujo que representa el conjunto de datos. Para facilitar esta tarea, escriba `Draw` en el **búsqueda** cuadro en la esquina superior derecha de la **lista de eventos gráficos** ventana. Con esto se filtra la lista para que solo incluya los eventos que tienen la palabra “Draw” en sus títulos. En este escenario, verá que se produjeron los siguientes eventos de dibujo:  
  
     ![La lista de eventos &#40;EL&#41; muestra eventos de dibujo. ] (media/gfx_diag_demo_compute_shader_fluid_step_2.png "gfx_diag_demo_compute_shader_fluid_step_2")  
  
3.  Desplácese por cada evento de dibujo mientras observa el destino de representación en la pestaña del documento de registro de gráficos.  
  
4.  Deténgase cuando el destino de representación muestre por primera vez el conjunto de datos representado. En este escenario, el conjunto de datos se representa en el primer evento de dibujo. Se muestra el error de la simulación:  
  
     ![Este evento draw presenta el conjunto de datos de simulación. ] (media/gfx_diag_demo_compute_shader_fluid_step_3.png "gfx_diag_demo_compute_shader_fluid_step_3")  
  
5.  Ahora inspeccione la **lista de eventos gráficos** para el `Dispatch` eventos que actualiza la simulación. Dado que es probable que la simulación se actualice antes de representarse, puede concentrarse primero en los eventos `Dispatch` que ocurren antes del evento de dibujo que representa los resultados. Para facilitar esta tarea, modifique la **búsqueda** cuadro leer `Draw;Dispatch;CSSetShader(`. De este modo, la lista se filtra para que también contenga los eventos `Dispatch` y `CSSetShader`, además de los eventos de dibujo. En este escenario, verá que se produjeron varios eventos `Dispatch` antes que el evento de dibujo:  
  
     ![Muestra eventos de dibujo, Dispatch y CSSetShader](media/gfx_diag_demo_compute_shader_fluid_step_4.png "gfx_diag_demo_compute_shader_fluid_step_4")  
  
 Ahora que ya sabe cuáles son los eventos `Dispatch` que podrían corresponderse con el problema, puede examinarlos con más detalle.  
  
#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Para determinar qué sombreador de cálculo se ejecuta con una llamada Dispatch  
  
1.  En el **diagnóstico de gráficos** barra de herramientas, elija **pila de llamadas de eventos** para abrir el **pila de llamadas de eventos de gráficos** ventana.  
  
2.  Comenzando desde el evento de dibujo que representa los resultados de la simulación, desplácese hacia atrás por cada evento `CSSetShader` anterior. A continuación, en el **pila de llamadas de eventos de gráficos** ventana, elija la función de más arriba para ir al sitio de llamada. En el sitio de llamada, puede usar el primer parámetro de la [CSSetShader](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-cssetshader) función llamada para determinar qué cálculo sombreador se ejecuta con el próximo `Dispatch` eventos.  
  
 En este escenario, hay tres pares de eventos `CSSetShader` y `Dispatch` en cada fotograma. Comenzando desde atrás, el tercer par representa el paso de integración (donde las partículas fluidas se mueven realmente), el segundo par representa el paso de cálculo de fuerza (donde se calculan las fuerzas que afectan a cada partícula) y el primer par representa el paso de cálculo de densidad.  
  
#### <a name="to-debug-the-compute-shader"></a>Para depurar al sombreador de cálculo  
  
1.  En el **diagnóstico de gráficos** barra de herramientas, elija **etapas de canalización** para abrir el **etapas de canalización de gráficos** ventana.  
  
2.  Seleccione el tercer `Dispatch` eventos (lo que precede inmediatamente al evento de dibujo) y, a continuación, en el **etapas de canalización de gráficos** ventana, en el **sombreador de cálculo** almacenar provisionalmente, elija  **Iniciar la depuración**.  
  
     ![Selección del tercer evento Dispatch en la EL.](media/gfx_diag_demo_compute_shader_fluid_step_6.png "gfx_diag_demo_compute_shader_fluid_step_6")  
  
     El depurador de HLSL se inicia en el sombreador que realiza el paso de la integración.  
  
3.  Examine el código fuente del sombreador de cálculo en el paso de integración y busque el origen del error. Cuando use el diagnóstico de gráficos para depurar el código del sombreador de cálculo de HLSL, puede ejecutar el código paso a paso y usar otras herramientas de depuración conocidas como las ventanas Inspección. En este escenario, no parece que haya un error en el sombreador de cálculo que realiza el paso de integración.  
  
     ![Depuración del sombreador de cálculo IntegrateCS. ] (media/gfx_diag_demo_compute_shader_fluid_step_7.png "gfx_diag_demo_compute_shader_fluid_step_7")  
  
4.  Para detener la depuración del sombreador de cálculo, en el **depurar** barra de herramientas, elija **Detener depuración** (teclado: Mayús + F5).  
  
5.  A continuación, seleccione el segundo evento `Dispatch` e inicie la depuración del sombreador de cálculo tal y como hizo en el paso anterior.  
  
     ![Selección del segundo evento Dispatch en la EL.](media/gfx_diag_demo_compute_shader_fluid_step_8.png "gfx_diag_demo_compute_shader_fluid_step_8")  
  
     El depurador de HLSL se inicia en el sombreador que calcula las fuerzas que actúan sobre cada partícula de fluido.  
  
6.  Examine el código fuente del sombreador de cálculo en el paso de cálculo de fuerza. En este caso, se determina que aquí está el origen del error.  
  
     ![Depurar el ForceCS&#95;sombreador de cálculo Simple. ] (media/gfx_diag_demo_compute_shader_fluid_step_9.png "gfx_diag_demo_compute_shader_fluid_step_9")  
  
 Después de determinar la ubicación del error, puede detener la depuración y modificar el código fuente de sombreador de cálculo para calcular correctamente la distancia entre las partículas interactivas. En este escenario, simplemente se cambia la línea de `float2 diff = N_position + P_position;` a `float2 diff = N_position - P_position;`:  
  
 ![El proceso corregido&#45;código del sombreador. ] (media/gfx_diag_demo_compute_shader_fluid_step_10.png "gfx_diag_demo_compute_shader_fluid_step_10")  
  
 En este escenario, dado que los sombreadores de cálculo se compilan en tiempo de ejecución, reinicie la aplicación después de realizar los cambios para observar cómo afectan a la simulación. No es necesario que vuelva a compilar la aplicación. Cuando ejecute la aplicación, verá que la simulación se comporta ahora correctamente.  
  
 ![El fluido simulado se comporta correctamente. ] (media/gfx_diag_demo_compute_shader_fluid_resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")