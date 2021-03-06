---
title: Análisis del uso de CPU en el Generador de perfiles de rendimiento
description: Obtenga más información sobre la herramienta de rendimiento Uso de CPU, que muestra el tiempo de la CPU y el porcentaje dedicado a ejecutar código en las aplicaciones de C++, C#, Visual Basic y JavaScript.
ms.custom: SEO-VS-2020
ms.date: 04/02/2020
ms.topic: how-to
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a223a2007d62b84f06191c71523b861f94efe3d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956131"
---
# <a name="analyze-cpu-usage-without-debugging-in-the-performance-profiler"></a>Análisis del uso de CPU sin depurar en el Generador de perfiles de rendimiento

Una buena forma de comenzar a investigar los problemas de rendimiento de la aplicación es entender el uso de CPU. La herramienta de rendimiento **Uso de CPU** muestra el tiempo de CPU y porcentaje dedicado a ejecutar código en las aplicaciones de C++, C#, Visual Basic y JavaScript.

La herramienta Uso de CPU puede ejecutarse en un proyecto de Visual Studio abierto, en una aplicación instalada de Microsoft Store, o conectarse a una aplicación o un proceso en ejecución. Puede ejecutar la herramienta Uso de CPU con o sin depuración. Para obtener más información, vea [Ejecutar herramientas de generación de perfiles con o sin el depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

En las siguientes instrucciones se muestra cómo usar la herramienta Uso de CPU sin el depurador, mediante el Generador de perfiles de rendimiento de Visual Studio. Los ejemplos usan una compilación de versión en un equipo local. Las compilaciones de versión proporcionan la mejor vista de rendimiento de la aplicación real. Para analizar el uso de CPU con compilaciones de depuración (depurador asociado), vea [Guía básica para la generación de perfiles de rendimiento](../profiling/beginners-guide-to-performance-profiling.md).

Por lo general, el equipo local replica mejor la ejecución de aplicaciones instaladas. Para recopilar datos de un dispositivo remoto, ejecute la aplicación directamente en el dispositivo en lugar de en una Conexión a Escritorio remoto.

>[!NOTE]
>Se requiere Windows 7 o posterior para usar el [Generador de perfiles de rendimiento](../profiling/profiling-feature-tour.md).

## <a name="collect-cpu-usage-data"></a>Recopilar datos de Uso de CPU

1. En el proyecto de Visual Studio, establezca la configuración de la solución en **Versión** y seleccione **Depurador local de Windows** (o **Equipo local**) como el destino de implementación.

    ![Selección de Versión y Máquina local](../profiling/media/cpuuse_selectreleaselocalmachine.png "Selección de Versión y Máquina local")

1. Seleccione **Depurar** > **Generador de perfiles de rendimiento**.

1. En **Herramientas disponibles** seleccione **Uso de CPU** y después **Iniciar**.

    ![Selección de Uso de CPU](../profiling/media/cpuuse_lib_choosecpuusage.png "Selección de Uso de CPU")

4. Después de que se inicie la aplicación, comienza la sesión de diagnóstico y muestra datos de uso de CPU. Cuando haya terminado de recopilar datos, haga clic en **Detener recopilación**.

   ![Detención de la recopilación de datos de uso de CPU](../profiling/media/cpu_use_wt_stopcollection.png "Detención de la recopilación de datos de uso de CPU")

   La herramienta Uso de CPU analiza y muestra el informe.

   ![Informe de uso de CPU](../profiling/media/cpu_use_wt_report.png "Informe de uso de CPU")

## <a name="analyze-the-cpu-usage-report"></a>Analizar el informe de Uso de CPU

El informe de diagnóstico se ordena por el **Total de CPU**, de mayor a menor. Puede cambiar el criterio de ordenación o la columna de ordenación seleccionando los encabezados de columna. Use la lista desplegable **Filtro** para seleccionar o anular la selección de subprocesos para mostrar, y use el cuadro **Búsqueda** para buscar un subproceso o un nodo concreto.

::: moniker range=">=vs-2019"
A partir de Visual Studio 2019, puede hacer clic en los botones **Expandir ruta de acceso activa** y **Mostrar ruta de acceso activa** para ver las llamadas de función que usan el porcentaje más alto de CPU en la vista de árbol de las llamadas.
::: moniker-end

### <a name="cpu-usage-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a> Columnas de datos de uso de CPU

|NOMBRE|Descripción|
|-|-|
|**Total de CPU [unidad, porcentaje]**|![Porcentaje de ecuación de datos total](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Los milisegundos y el porcentaje de CPU que usaron las llamadas a la función y las funciones llamadas por la función en el intervalo de tiempo seleccionado. Esto no es lo mismo que el gráfico de línea cronológica **Utilización de CPU**, que compara la actividad total de CPU en un intervalo de tiempo con el total de CPU disponible.|
|**CPU propia [unidad, porcentaje]**|![Porcentaje de autoecuación](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Los milisegundos y el porcentaje de CPU que usaron las llamadas a la función en el intervalo de tiempo seleccionado, sin incluir las funciones llamadas por la función.|
|**Módulo**|El nombre del módulo que contiene la función.

### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a> Árbol de llamadas de Uso de CPU

Para ver el árbol de llamadas, seleccione el nodo primario en el informe. La página **Uso de CPU** se abre para la vista **Llamador y destinatario**. En la lista desplegable **Vista actual** seleccione **Árbol de llamadas**.

#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a> Estructura del árbol de llamadas

::: moniker range=">=vs-2019"
![Estructura del árbol de llamadas](../profiling/media/vs-2019/cpu-use-wt-getmaxnumbercalltree-annotated.png "Estructura del árbol de llamadas")
::: moniker-end
::: moniker range="vs-2017"
![Estructura del árbol de llamadas](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "Estructura del árbol de llamadas")
::: moniker-end

|Imagen|Descripción|
|-|-|
|![Paso 1](../profiling/media/procguid_1.png "ProcGuid_1")|El nodo de nivel superior de los árboles de llamadas de Uso de CPU es un pseudonodo.|
|![Paso 2](../profiling/media/procguid_2.png "ProcGuid_2")|En la mayoría de las aplicaciones, cuando se desactiva la opción **Mostrar código externo**, el nodo de segundo nivel es un nodo **[Código externo]** . El nodo contiene el código del sistema y del marco que inicia y detiene la aplicación, dibuja la interfaz de usuario, controla la programación de subprocesos y ofrece otros servicios de bajo nivel a la aplicación.|
|![Paso 3](../profiling/media/procguid_3.png "ProcGuid_3")|Los elementos secundarios del nodo de segundo nivel son los métodos de código de usuario y las rutinas asíncronas llamados o creados por el sistema de segundo nivel y el código de Framework.|
|![Paso 4](../profiling/media/procguid_4.png "ProcGuid_4")|Los nodos secundarios de un método contienen datos únicamente de las llamadas del método principal. Cuando está deshabilitada la opción **Mostrar código externo** , los métodos de aplicación también pueden contener un nodo **[Código externo]** .|

#### <a name="external-code"></a><a name="BKMK_External_Code"></a> Código externo

Las funciones del sistema y del marco que ejecuta el código se llaman *código externo*. Las funciones de código externo inician y detienen la aplicación, dibujan la interfaz de usuario, controlan los subprocesos y proporcionan otros servicios de bajo nivel a la aplicación. En la mayoría de los casos no le interesará el código externo, por lo que el árbol de llamadas de Uso de CPU reúne las funciones externas de un método de usuario en un nodo **[Código externo]** .

Para ver las rutas de llamada de código externo, en la página de informe de diagnóstico principal (panel derecho), seleccione **Mostrar código externo** en la lista desplegable **Filtro** y después haga clic en **Aplicar**. Después, la vista **Árbol de llamadas** de la página **Uso de CPU** expande las llamadas a código externo. (La lista desplegable **Filtro** está disponible en la página principal de diagnóstico, no en las vistas detalladas).

![Mostrar código externo](../profiling/media/cpu_use_wt_filterview.png "Mostrar código externo")

Muchas cadenas de llamadas de código externo están profundamente anidadas, así que el ancho de la cadena puede superar el ancho de pantalla de la columna **Nombre de la función**. Los nombres de función aparecen como **...** .

![Código externo anidado en el árbol de llamadas](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "Código externo anidado en el árbol de llamadas")

Para encontrar un nombre de función que está buscando, use el cuadro de búsqueda. Mantenga el mouse sobre la línea seleccionada o use la barra de desplazamiento horizontal para ver los datos.

::: moniker range=">=vs-2019"
![Búsqueda de código externo anidado](../profiling/media/vs-2019/cpu-use-wt-showexternalcodetoowide-found.png "Búsqueda de código externo anidado")
::: moniker-end
::: moniker range="vs-2017"
![Búsqueda de código externo anidado](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "Búsqueda de código externo anidado")
::: moniker-end

### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Funciones asincrónicas en el árbol de llamadas de Uso de CPU

 Cuando el compilador encuentra un método asincrónico, crea una clase oculta para controlar la ejecución del método. Conceptualmente, la clase es una máquina de estados. La clase tiene funciones generadas por el compilador que llaman asincrónicamente a los métodos originales, las devoluciones de llamada, el programador y los iteradores necesarios para ejecutarlos. Cuando un método principal llama al método original, el compilador quita al método del contexto de ejecución del elemento principal y ejecuta los métodos de la clase oculta en el contexto del código del sistema y Framework que controla la ejecución de la aplicación. A menudo, aunque no siempre, los métodos asincrónicos se ejecutan en uno o varios subprocesos diferentes. Este código aparece en el árbol de llamadas de **Uso de CPU** como elementos secundarios del nodo **[Código externo]** que se encuentra justo debajo del nodo superior del árbol.

En el siguiente ejemplo, los dos primeros nodos bajo **[Código externo]** son los métodos generados por el compilador de la clase de la máquina de estados. El tercer nodo es la llamada al método original.

![Nodo asincrónico](media/cpu_use_wt_getmaxnumberasync_selected.png "Nodo asincrónico")

Expanda los métodos generados para mostrar lo que está sucediendo:

![Nodo asincrónico expandido](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "Nodo asincrónico expandido")

- `MainPage::GetMaxNumberAsyncButton_Click` solo administra una lista de valores de la tarea, calcula el valor máximo de los resultados y muestra el resultado.

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` muestra la actividad necesaria para programar e iniciar las 48 tareas que incluyen la llamada en `GetNumberAsync`.

- `MainPage::<GetNumberAsync>b__b` muestra la actividad de las tareas que llaman a `GetNumber`.
