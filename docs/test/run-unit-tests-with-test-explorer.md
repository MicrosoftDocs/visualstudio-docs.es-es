---
title: Ejecución y depuración de pruebas unitarias con el Explorador de pruebas
description: Obtenga información sobre cómo ejecutar pruebas con el Explorador de pruebas en Visual Studio. En este tema se explica cómo habilitar ejecuciones de pruebas automáticas después de la compilación, ver los resultados de las pruebas, agrupar y filtrar la lista de pruebas, crear listas de reproducción, depurar las pruebas y usar métodos abreviados de pruebas.
ms.date: 07/29/2019
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27ca8a39d39fcc8b4e5ddca2cbedf72e44c6cc81
ms.sourcegitcommit: 689ba54ea14257d13031de881f5d4fe937a36f56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342453"
---
# <a name="run-unit-tests-with-test-explorer"></a>Ejecutar pruebas unitarias con el Explorador de pruebas

Use el Explorador de pruebas para ejecutar pruebas unitarias en proyectos de Visual Studio o de terceros. También puede usar el Explorador de pruebas para agrupar las pruebas en categorías, filtrar la lista de pruebas y crear, guardar y ejecutar listas de reproducción de pruebas. Puede depurar las pruebas y analizar la cobertura de código y el rendimiento de la prueba.

Visual Studio incluye los marcos de pruebas unitarias de Microsoft para código administrado y nativo. No obstante, el Explorador de pruebas también puede ejecutar cualquier marco de pruebas unitarias que haya implementado un adaptador de este explorador. Para más información sobre cómo instalar los marcos de pruebas unitarias de terceros, vea [Instalar marcos de prueba unitaria de terceros](../test/install-third-party-unit-test-frameworks.md).

El **Explorador de pruebas** puede ejecutar pruebas de varios proyectos de prueba en una solución y desde las clases de prueba que forman parte de los proyectos de código de producción. En los proyectos de prueba pueden usarse marcos de pruebas unitarias diferentes. Cuando el código sometido a prueba está escrito para .NET, el proyecto de prueba puede escribirse en cualquier lenguaje que también tenga .NET como destino, independientemente del lenguaje del código de destino. Los proyectos de código de C/C ++ nativos deben probarse con el marco de pruebas unitarias de C++. Para más información, vea [Escribir pruebas unitarias para C/C++ en Visual Studio](writing-unit-tests-for-c-cpp.md).

## <a name="run-tests-in-test-explorer"></a>Ejecutar pruebas en Explorador de pruebas


Al compilar el proyecto de prueba, las pruebas aparecen en el Explorador de pruebas. Si el Explorador de pruebas no está visible, elija **Prueba** en el menú de Visual Studio, elija **Ventanas**y, después, **Explorador de pruebas**.


::: moniker range="vs-2017"
![Explorador de pruebas unitarias](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Explorador de pruebas](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Al ejecutar, escribir y volver a ejecutar las pruebas, el Explorador de pruebas muestra los resultados en los grupos predeterminados de **Pruebas no superadas**, **Pruebas superadas**, **Pruebas omitidas** y **Pruebas no ejecutadas**. Puede cambiar la manera en que el Explorador de pruebas agrupa las pruebas.
::: moniker-end
::: moniker range=">=vs-2019"
Cuando ejecute, escriba y vuelva a ejecutar las pruebas, el Explorador de pruebas mostrará los resultados en una agrupación predeterminada de **Proyecto**, **Espacio de nombres** y **Clase**. Puede cambiar la manera en que el Explorador de pruebas agrupa las pruebas.
::: moniker-end

Desde la barra de herramientas del **Explorador de pruebas** puede realizar gran parte del trabajo de búsqueda, organización y ejecución de las pruebas.

::: moniker range="vs-2017"
![Ejecutar pruebas desde la barra de herramientas del Explorador de pruebas](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Ejecutar pruebas desde la barra de herramientas del Explorador de pruebas](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Ejecutar pruebas

::: moniker range="vs-2017"
Puede ejecutar todas las pruebas de la solución, todas las pruebas de un grupo o un conjunto de pruebas seleccionado. Realice una de las siguientes acciones:

- Para ejecutar todas las pruebas de una solución, elija **Ejecutar todas**.

- Para ejecutar todas las pruebas de un grupo predeterminado, elija **Ejecutar** y el grupo en el menú.

- Seleccione las pruebas individuales que quiera ejecutar, abra el menú contextual de la prueba seleccionada y seleccione **Ejecutar pruebas seleccionadas**.

- Si las pruebas individuales no tienen ninguna dependencia que impida que se ejecuten en cualquier orden, active la ejecución de pruebas paralelas con el botón de alternancia ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png) en la barra de herramientas. Esto puede reducir considerablemente el tiempo necesario para ejecutar todas las pruebas.

Según se vayan ejecutando las pruebas, se animará la **barra de superado o no superado** en la parte superior de la ventana del **Explorador de pruebas**. Al finalizar la ejecución de las pruebas, la **barra de superado o no superado** se mostrará en color verde si se superan todas las pruebas. En caso contrario, se volverá de color rojo.
::: moniker-end
::: moniker range=">=vs-2019"
Puede ejecutar todas las pruebas de la solución, todas las pruebas de un grupo o un conjunto de pruebas seleccionado. Realice una de las siguientes acciones:

- Para ejecutar todas las pruebas de una solución, elija el icono **Ejecutar todas**.

- Para ejecutar todas las pruebas de un grupo predeterminado, elija el icono **Ejecutar** y el grupo en el menú.

- Seleccione las pruebas individuales que quiera ejecutar, abra el menú contextual de la prueba seleccionada y seleccione **Ejecutar pruebas seleccionadas**.

- Si las pruebas individuales no tienen ninguna dependencia que impida que se ejecuten en cualquier orden, active la ejecución de pruebas paralelas en el menú de configuración de la barra de herramientas. Esto puede reducir considerablemente el tiempo necesario para ejecutar todas las pruebas.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Ejecutar pruebas después de cada compilación
::: moniker range="vs-2017"
|Botón|DESCRIPCIÓN|
|-|-|
|![Ejecutar después de compilar](../test/media/ute_runafterbuild_btn.png)|Para ejecutar pruebas unitarias después de cada compilación local, elija **Prueba** en el menú estándar, o **Ejecutar pruebas después de compilar** en la barra de herramientas del **Explorador de pruebas**.|

> [!NOTE]
> La ejecución de pruebas unitarias después de cada compilación requiere Visual Studio 2017 Enterprise o Visual Studio 2019. En Visual Studio 2019 se incluyen las ediciones Community, Professional y Enterprise.
::: moniker-end
::: moniker range=">=vs-2019"
Para ejecutar las pruebas unitarias después de cada compilación local, abra el icono de configuración en la barra de herramientas del Explorador de pruebas y seleccione **Ejecutar pruebas después de compilar**.
::: moniker-end

## <a name="view-test-results"></a>Ver los resultados de las pruebas

Al ejecutar, escribir y volver a ejecutar las pruebas, el Explorador de pruebas muestra los resultados en los grupos de **Pruebas no superadas**, **Pruebas superadas**, **Pruebas omitidas** y **Pruebas no ejecutadas**. El panel de detalles de la parte inferior o lateral del Explorador de pruebas muestra un resumen de la serie de pruebas.

### <a name="view-test-details"></a>Ver detalles de la prueba

Para ver los detalles de una prueba individual, selecciónela.

::: moniker range="vs-2017"
![Detalles de ejecución de las pruebas](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Detalles de ejecución de las pruebas](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

El panel de detalles de la prueba muestra la información siguiente:

- El nombre de archivo de origen y el número de línea del método de prueba.

- Estado de la prueba.

- El tiempo que ha tardado en ejecutarse el método de prueba.

Si la prueba no se supera, en el panel de detalles se mostrará también:

- El mensaje que ha devuelto el marco de pruebas unitarias para la prueba.

- El seguimiento de la pila en el momento en que la prueba generó el error.

### <a name="view-the-source-code-of-a-test-method"></a>Ver el código fuente de un método de prueba

Para mostrar el código fuente de un método de prueba en el editor de Visual Studio, seleccione la prueba y haga clic en **Abrir prueba** en el menú contextual (teclado: **F12**).

## <a name="group-and-filter-the-test-list"></a>Agrupar y filtrar la lista de pruebas

El Explorador de pruebas permite agrupar las pruebas en las categorías predefinidas. En la mayoría de los marcos de pruebas unitarias que se ejecutan en el Explorador de pruebas podrá definir las categorías y los pares categoría-valor para agrupar las pruebas que desee. Para filtrar la lista de pruebas, también puede establecer coincidencias entre las cadenas y las propiedades de las pruebas.

### <a name="group-tests-in-the-test-list"></a>Agrupar pruebas en la lista de pruebas

::: moniker range="vs-2017"
Para cambiar la forma en que se organizan las pruebas, haga clic en la flecha abajo situada junto al botón **Agrupar por** ![Botón de grupo Explorador de pruebas](../test/media/ute_groupby_btn.png) y seleccione un nuevo criterio de agrupación.

![Agrupar pruebas por categoría en el Explorador de pruebas](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
El Explorador de pruebas le permite agrupar las pruebas en una jerarquía. La agrupación de jerarquías predeterminada es **Proyecto**, **Espacio de nombres** y, luego, **Clase**. Para cambiar la manera en que se organizan las pruebas, elije el botón **Agrupar por** ![botón de grupo Explorador de pruebas](../test/media/ute_groupby_btn.png) y seleccione un nuevo criterio de agrupación.

![Agrupar pruebas por categoría en el Explorador de pruebas](../test/media/vs-2019/test-explorer-groupby-162.png)

Puede definir sus propios niveles de la jerarquía y del grupo por **Estado** y, luego, **Clase**, por ejemplo, si selecciona las opciones Agrupar por en el orden que prefiera.

![Agrupar por estado y luego clase](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Grupos del Explorador de pruebas

::: moniker range="vs-2017"
|Agrupar|DESCRIPCIÓN|
|-|-----------------|
|**Duración**|Agrupa las pruebas por tiempo de ejecución: **Rápido**, **Medio**y **Lento**.|
|**Resultado**|Agrupa las pruebas por resultados de ejecución: **Pruebas no superadas**, **Pruebas omitidas**y **Pruebas superadas**.|
|**Rasgos**|Agrupa las pruebas por los pares categoría-valor definidos. La sintaxis para especificar los valores y las categorías de rasgo se define desde el marco de pruebas unitarias.|
|**Proyecto**|Agrupa las pruebas por el nombre de los proyectos.|
::: moniker-end
::: moniker range=">=vs-2019"
|Agrupar|DESCRIPCIÓN|
|-|-----------------|
|**Duración**|Agrupa las pruebas por tiempo de ejecución: **Rápido**, **Medio**y **Lento**.|
|**Estado**|Agrupa las pruebas por resultados de ejecución: **Pruebas no superadas**, **Pruebas omitidas**, **Pruebas superadas**, **No ejecutadas**.|
|**Marco de destino** | Agrupa las pruebas por marco de destino de sus proyectos. |
|**Espacio de nombres**|Agrupa las pruebas por espacio de nombres contenedor.|
|**Proyecto**|Agrupa las pruebas por proyecto contenedor.|
|**Clase**|Agrupa las pruebas por clase contenedora.|
::: moniker-end

### <a name="traits"></a>Rasgos

Por lo general, un rasgo es un par nombre-valor de categoría, pero también puede ser una sola categoría. Los rasgos se pueden asignar a los métodos identificados como métodos de prueba desde el marco de pruebas unitarias. Un marco de pruebas unitarias puede definir categorías de rasgo. Si lo desea, puede agregar valores a las categorías de rasgo para definir sus propios pares nombre-valor de categoría. La sintaxis para especificar los valores y las categorías de rasgo se define desde el marco de pruebas unitarias.

**Rasgos del marco de pruebas unitarias de Microsoft para código administrado**

En el marco de pruebas unitarias de Microsoft para aplicaciones administradas, el par nombre-valor de rasgo se define en un atributo  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> . El marco de pruebas también contiene estos rasgos predefinidos:

|Rasgo|DESCRIPCIÓN|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|La categoría de propietario se define desde el marco de pruebas unitarias y requiere un valor de cadena del propietario.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|La categoría de prioridad se define desde el marco de pruebas unitarias y requiere un valor entero de la prioridad.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|El atributo TestCategory permite proporcionar una categoría sin ningún valor.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|El atributo TestProperty permite definir un par categoría-valor de rasgo.|


**Rasgos del marco de pruebas unitarias de Microsoft para C++**

Vea [How to use the Microsoft Unit Testing Framework for C++](how-to-use-microsoft-test-framework-for-cpp.md) (Cómo usar el marco de pruebas unitarias de Microsoft para C++).

## <a name="create-custom-playlists"></a>Crear listas de reproducción personalizadas

::: moniker range="vs-2017"
Puede crear y guardar una lista de pruebas que desea ejecutar o ver como grupo. Al seleccionar una lista de reproducción, las pruebas de la lista aparecerán en el Explorador de pruebas. Si lo desea, puede agregar una prueba a varias listas de reproducción. Para acceder a todas las pruebas de un proyecto, elija la lista de reproducción predeterminada **Todas las pruebas** .

![Elegir una lista de reproducción](../test/media/ute_playlist.png)

**Para crear una lista de reproducción**, elija una o varias pruebas en el Explorador de pruebas. En el menú contextual, seleccione **Agregar a lista de reproducción** > **Nueva lista de reproducción**. Guarde el archivo con la ubicación y el nombre especificados en el cuadro de diálogo **Crear nueva lista de reproducción** .

**Para agregar pruebas a una lista de reproducción**, elija una o varias pruebas en el Explorador de pruebas. En el menú contextual, haga clic en **Agregar a lista de reproducción** y, después, seleccione la lista de reproducción a la que quiera agregar las pruebas.

**Para abrir una lista de reproducción**, elija **Prueba** > **Lista de reproducción** en el menú de Visual Studio, y seleccione un elemento entre las listas de reproducción usadas recientemente. O bien, elija **Abrir lista de reproducción** para especificar el nombre y la ubicación de la lista de reproducción específica.

Si las pruebas individuales no tienen ninguna dependencia que impida que se ejecuten en cualquier orden, active la ejecución de pruebas paralelas con el botón de alternancia ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png) en la barra de herramientas. Esto puede reducir considerablemente el tiempo necesario para ejecutar todas las pruebas.
::: moniker-end
::: moniker range=">=vs-2019"
Puede crear y guardar una lista de pruebas que desea ejecutar o ver como grupo. Cuando seleccione una lista de reproducción, las pruebas de la lista aparecerá en una nueva pestaña del Explorador de pruebas. Puede agregar una prueba a más de una lista de reproducción.

**Para crear una lista de reproducción**, elija una o varias pruebas en el Explorador de pruebas. En el menú contextual, seleccione **Agregar a lista de reproducción** > **Nueva lista de reproducción**.

![Creación de una lista de reproducción](../test/media/vs-2019/test-explorer-playlist-16-2.png)

La lista de reproducción en una nueva pestaña del Explorador de pruebas. Puede usar esta lista de reproducción una vez y luego descartarla, o bien puede hacer clic en el botón **Guardar** en la barra de herramientas de la ventana de la lista de reproducción y, luego, seleccione un nombre y una ubicación para guardar la lista de reproducción.

![La lista de reproducción se abre en una nueva pestaña del Explorador de pruebas](../test/media/vs-2019/test-explorer-playlist-tab-16-2.png)

**Para crear una lista de reproducción**, elija una o varias pruebas en el Explorador de pruebas. Haga clic con el botón derecho y elija **Agregar a lista de reproducción** > **Nueva lista de reproducción**.

**Para abrir una lista de reproducción**, elija el icono de lista de reproducción en la barra de herramientas de Visual Studio y seleccione un archivo de lista de reproducción guardado anteriormente desde el menú.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Columnas del Explorador de pruebas

Los [grupos](#test-explorer-groups) también están disponibles como columnas en el Explorador de pruebas, junto con Rasgo, Seguimiento de la pila, Mensaje de error y Nombre completo. La mayoría de las columnas no están visibles de manera predeterminada y es posible personalizar qué columnas se ven y el orden en que se muestran.

![Agrupar por estado y luego clase](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Filtrar, ordenar y reorganizar columnas de prueba

Las columnas se pueden filtrar, ordenar y reorganizar.
* Para filtrar según rasgos específicos, haga clic en el icono de filtro ubicado en la parte superior de la columna Rasgos.

  ![Filtro de columna](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Para cambiar el orden de las columnas, haga clic en un encabezado de columna y arrástrelo a la izquierda o a la derecha.

* Para ordenar una columna, haga clic en el encabezado de la columna. No todas las columnas se pueden ordenar. También puede ordenar por una columna secundaria si mantiene presionada la tecla **Mayús** y hace clic en un encabezado de columna adicional.

  ![Orden de columna](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>Buscar y filtrar la lista de pruebas

También puede limitar los métodos de prueba en los proyectos que vea y ejecute con los filtros de búsqueda del Explorador de pruebas.

Si escribe una cadena en el cuadro de búsqueda del **Explorador de pruebas** y presiona **Entrar**, la lista de pruebas se filtrará para mostrar solo las pruebas cuyos nombres completos contengan dicha cadena.

Para filtrar por otros criterios:

1. Abra la lista desplegable situada a la derecha del cuadro de búsqueda.

2. Elija un criterio nuevo.

3. Escriba el valor de filtro entre comillas. Si quiere buscar una coincidencia exacta en la cadena en lugar de una coincidencia que contenga el valor, use un signo igual (=) en lugar de dos puntos (:).

::: moniker range="vs-2017"
![Filtrar pruebas en el Explorador de pruebas](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Filtrar pruebas en el Explorador de pruebas](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> Las búsquedas distinguen entre mayúsculas y minúsculas, y coinciden con la cadena especificada en cualquier parte del valor de criterios.

::: moniker range="vs-2017"
|Calificador:|DESCRIPCIÓN|
|-|-----------------|
|**Rasgo**|Busca coincidencias en el valor y en la categoría de rasgo. La sintaxis para especificar los valores y las categorías de rasgo se define en el marco de pruebas unitarias.|
|**Proyecto**|Busca coincidencias en los nombres de proyecto de prueba.|
|**Mensaje de error**|Busca coincidencias en los mensajes de error definidos por el usuario que devuelven las aserciones con errores.|
|**Ruta de acceso del archivo**|Busca coincidencias en el nombre de archivo completo de los archivos de origen de prueba.|
|**Nombre completo**|Busca coincidencias en el nombre completo de los métodos, las clases y los espacios de nombres de prueba.|
|**Salida**|Busca en los mensajes de error definidos por el usuario que se escriben en los resultados estándar (stdout) o en los errores estándar (stderr). La sintaxis para especificar los mensajes de salida se define en el marco de pruebas unitarias.|
|**Resultado**|Busca coincidencias en los nombres de categoría del Explorador de pruebas: **Pruebas no superadas**, **Pruebas omitidas**y **Pruebas superadas**.|
::: moniker-end
::: moniker range=">=vs-2019"
|Calificador:|DESCRIPCIÓN|
|-|-----------------|
|**Estado**|Busca coincidencias en los nombres de categoría del Explorador de pruebas: **Pruebas no superadas**, **Pruebas omitidas**y **Pruebas superadas**.|
|**Rasgos**|Busca coincidencias en el valor y en la categoría de rasgo. La sintaxis para especificar los valores y las categorías de rasgo se define en el marco de pruebas unitarias.|
|**Nombre completo**|Busca coincidencias en el nombre completo de los métodos, las clases y los espacios de nombres de prueba.|
|**Proyecto**|Busca coincidencias en los nombres de proyecto de prueba.|
|**Marco de destino**|Busca coincidencias en los nombres de categoría del Explorador de pruebas: **Pruebas no superadas**, **Pruebas omitidas**y **Pruebas superadas**.|
|**Espacio de nombres**|Busca coincidencias en los espacios de nombres de prueba.|
|**Clase**|Busca coincidencias en los nombres de clase de prueba.|
::: moniker-end

Puede excluir un subconjunto de resultados de un filtro con la sintaxis siguiente:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Por ejemplo, `FullName:"MyClass" - FullName:"PerfTest"` devuelve todas las pruebas que incluyen "MyClass" en el nombre, excepto las que también incluyan "PerfTest".

## <a name="debug-and-analyze-unit-tests"></a>Depurar y analizar pruebas unitarias

Se puede usar el Explorador de pruebas para iniciar una sesión de depuración para las pruebas. La ejecución paso a paso del código con el depurador de Visual Studio permite avanzar y retroceder sin problemas entre las pruebas unitarias y el proyecto objeto de prueba. Para iniciar la depuración:

1. En el editor de Visual Studio, establezca un punto de interrupción en uno o varios métodos de prueba que desee depurar.

    > [!NOTE]
    > Dado que los métodos de prueba se pueden ejecutar en cualquier orden, establezca puntos de interrupción en todos los métodos de prueba que desee depurar.

2. En el Explorador de pruebas, seleccione los métodos de prueba y seleccione **Depurar pruebas seleccionadas** en el menú contextual.

   Para obtener más información sobre el depurador, vea [Depurar en Visual Studio](../debugger/debugger-feature-tour.md).

### <a name="diagnose-test-method-performance-issues"></a>Diagnosticar problemas de rendimiento del método de prueba

Para diagnosticar por qué tarda demasiado un método de prueba, selecciónelo en el Explorador de pruebas y, luego, elija **Profile Selected Test** (Prueba seleccionada de perfil) en el menú contextual. Vea [Explorador de rendimiento](../profiling/performance-explorer.md).

### <a name="analyze-unit-test-code-coverage"></a>Analizar la cobertura de código de prueba unitaria

Es posible determinar la cantidad de código de producto que las pruebas unitarias están probando realmente con la herramienta de cobertura de código de Visual Studio, disponible en la edición Visual Studio Enterprise. La cobertura de código se puede ejecutar en pruebas seleccionadas o en todas las pruebas de una solución.

Para ejecutar la cobertura de código en los métodos de prueba de una solución:

::: moniker range="vs-2017"

1. Seleccione **Prueba** en la barra de menús superior y luego **Analizar cobertura de código**.

2. En el submenú, elija uno de los comandos siguientes:

    - **Pruebas seleccionadas** ejecuta los métodos de prueba que ha seleccionado en el Explorador de pruebas.

    - **Todas las pruebas** ejecuta todos los métodos de prueba en la solución.

::: moniker-end

::: moniker range=">=vs-2019"

* Haga clic con el botón derecho en el Explorador de pruebas y seleccione **Analizar cobertura de código para las pruebas seleccionadas**.

::: moniker-end

La ventana **Resultados de la cobertura de código** muestra el porcentaje de bloques de código de producto que se han ejecutado por línea, función, clase, espacio de nombres y módulo.

Para obtener más información, vea [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Métodos abreviados de pruebas

Para ejecutar las pruebas desde el Explorador de pruebas, haga clic con el botón derecho en una prueba en el editor de código y seleccione **Ejecutar prueba**; o use los [métodos abreviados del Explorador de pruebas](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) predeterminados en Visual Studio. Algunos de los métodos abreviados dependen del contexto. Esto significa que ejecutan o depuran las pruebas en función de la posición del cursor en el editor de código. Si el cursor está dentro de un método de prueba, se ejecuta ese método de prueba. Si el cursor está en el nivel de clase, se ejecutan todas las pruebas de esa clase. Lo mismo sucede en el nivel de espacio de nombres.

|Comandos más frecuentes| Métodos abreviados de teclado|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**Ctrl**+**R**, **Ctrl**+**T**|
|TestExplorer.RunAllTestsInContext|**Ctrl**+**R**, **T**|
|TestExplorer.RunAllTests|**Ctrl**+**R**, **A**|
|TestExplorer.RepeatLastRun|**Ctrl**+**R**, **L**|

> [!NOTE]
> No se puede ejecutar una prueba en una clase abstracta, ya que las pruebas solo se definen en las clases abstractas, no se crean instancias. Para ejecutar pruebas en las clases abstractas, cree una clase que se derive de la clase abstracta.

## <a name="see-also"></a>Vea también

- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
- [Ejecutar una prueba unitaria como un proceso de 64 bits](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Preguntas más frecuentes sobre el Explorador de pruebas](test-explorer-faq.md)
