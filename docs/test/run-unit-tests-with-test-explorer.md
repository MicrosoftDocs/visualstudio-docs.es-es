---
title: Ejecutar pruebas unitarias con el Explorador de pruebas | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: eda6a63b8d6e10b3eec3139ffa29143b0b5733ba
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="run-unit-tests-with-test-explorer"></a>Ejecutar pruebas unitarias con el Explorador de pruebas

Use el **Explorador de pruebas** para ejecutar pruebas unitarias en proyectos de Visual Studio o de terceros. También puede usar el **Explorador de pruebas** para agrupar las pruebas en categorías, filtrar la lista de pruebas y crear, guardar y ejecutar listas de reproducción de pruebas. Puede depurar las pruebas y analizar la cobertura de código y el rendimiento de la prueba.

Visual Studio incluye los marcos de pruebas unitarias de Microsoft para código administrado y nativo. No obstante, el **Explorador de pruebas** también puede ejecutar cualquier marco de pruebas unitarias que haya implementado un adaptador de este explorador. Para más información sobre cómo instalar los marcos de pruebas unitarias de terceros, vea [Instalar marcos de prueba unitaria de terceros](../test/install-third-party-unit-test-frameworks.md).

El **Explorador de pruebas** puede ejecutar pruebas de varios proyectos de prueba en una solución y desde las clases de prueba que forman parte de los proyectos de código de producción. En los proyectos de prueba pueden usarse marcos de pruebas unitarias diferentes. Cuando se escribe el código sometido a prueba para .NET Framework, el proyecto de prueba puede escribirse en cualquier lenguaje que también contemple .NET Framework como destino, independientemente del lenguaje del código de destino. Los proyectos de código de C/C ++ nativos deben probarse con el marco de pruebas unitarias de C++. Para obtener más información, vea [Writing unit tests for C/C++](writing-unit-tests-for-c-cpp.md) (Escribir pruebas unitarias para C/C++).

## <a name="run-tests-in-test-explorer"></a>Ejecutar pruebas en Explorador de pruebas

Al compilar el proyecto de prueba, las pruebas aparecen en el Explorador de pruebas. Si el Explorador de pruebas no está visible, elija **Prueba** en el menú de Visual Studio, elija **Ventanas**y, después, **Explorador de pruebas**.

![Explorador de pruebas unitarias](../test/media/ute_failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

Al ejecutar, escribir y volver a ejecutar las pruebas, el Explorador de pruebas muestra los resultados en los grupos predeterminados de **Pruebas no superadas**, **Pruebas superadas**, **Pruebas omitidas** y **Pruebas no ejecutadas**. Puede cambiar la manera en que el Explorador de pruebas agrupa las pruebas.

Desde la barra de herramientas del Explorador de pruebas puede realizar gran parte del trabajo de búsqueda, organización y ejecución de las pruebas.

![Ejecutar pruebas desde la barra de herramientas del Explorador de pruebas](../test/media/ute_toolbar.png "UTE_ToolBar")

### <a name="run-tests"></a>Ejecutar pruebas

Puede ejecutar todas las pruebas de la solución, todas las pruebas de un grupo o un conjunto de pruebas seleccionado. Realice una de las siguientes acciones:

- Para ejecutar todas las pruebas de una solución, elija **Ejecutar todas**.

- Para ejecutar todas las pruebas de un grupo predeterminado, elija **Ejecutar...** y el grupo en el menú.

- Seleccione las pruebas individuales que desea ejecutar, abra el menú contextual de una prueba seleccionada y elija **Ejecutar pruebas seleccionadas**.

- Si las pruebas individuales no tienen ninguna dependencia que impida que se ejecuten en cualquier orden, active la ejecución de pruebas paralelas con el botón de alternancia ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png "UTE_parallelicon-small") en la barra de herramientas. Esto puede reducir considerablemente el tiempo necesario para ejecutar todas las pruebas.

Según se vayan ejecutando las pruebas, se animará la barra de superado o no superado en la parte superior de la ventana del Explorador de pruebas. Al finalizar la ejecución de las pruebas, la barra de superado o no superado se pondrá verde si se superan todas las pruebas. En caso contrario, se pondrá roja.

### <a name="run-tests-after-every-build"></a>Ejecutar pruebas después de cada compilación

|||
|-|-|
|![Ejecutar después de compilar](../test/media/ute_runafterbuild_btn.png)|Para ejecutar pruebas unitarias después de cada compilación local, elija **Prueba** en el menú estándar, o **Ejecutar pruebas después de compilar** en la barra de herramientas del Explorador de pruebas.|

## <a name="view-test-results"></a>Ver los resultados de las pruebas

Al ejecutar, escribir y volver a ejecutar las pruebas, el Explorador de pruebas muestra los resultados en los grupos de **Pruebas no superadas**, **Pruebas superadas**, **Pruebas omitidas** y **Pruebas no ejecutadas**. El panel de detalles de la parte inferior del Explorador de pruebas muestra un resumen de la ejecución de la prueba.

### <a name="view-test-details"></a>Ver detalles de la prueba

Para ver los detalles de una prueba individual, selecciónela.

![Detalles de ejecución de las pruebas](../test/media/ute_testdetails.png "UTE_TestDetails")

El panel de detalles de la prueba muestra la información siguiente:

- El nombre de archivo de origen y el número de línea del método de prueba.

- Estado de la prueba.

- El tiempo que ha tardado en ejecutarse el método de prueba.

Si la prueba no se supera, en el panel de detalles se mostrará también:

- El mensaje que ha devuelto el marco de pruebas unitarias para la prueba.

- El seguimiento de la pila en el momento en que la prueba generó el error.

### <a name="view-the-source-code-of-a-test-method"></a>Ver el código fuente de un método de prueba

 Para mostrar el código fuente de un método de prueba en el editor de Visual Studio, seleccione la prueba y elija **Abrir prueba** en el menú contextual (teclado: **F12**).

## <a name="group-and-filter-the-test-list"></a>Agrupar y filtrar la lista de pruebas

El Explorador de pruebas permite agrupar las pruebas en las categorías predefinidas. En la mayoría de los marcos de pruebas unitarias que se ejecutan en el Explorador de pruebas podrá definir las categorías y los pares categoría-valor para agrupar las pruebas que desee. Para filtrar la lista de pruebas, también puede establecer coincidencias entre las cadenas y las propiedades de las pruebas.

### <a name="group-tests-in-the-test-list"></a>Agrupar pruebas en la lista de pruebas

 Para cambiar la forma en que se organizan las pruebas, seleccione la flecha abajo situada junto al botón **Agrupar por** ![Botón de grupo Explorador de pruebas](../test/media/ute_groupby_btn.png "UTE_GroupBy_btn") y seleccione un nuevo criterio de agrupación.

 ![Agrupar pruebas por categoría en el Explorador de pruebas](../test/media/ute_groupbycategory.png "UTE_GroupByCategory")

### <a name="test-explorer-groups"></a>Grupos del Explorador de pruebas

|Agrupar|Description|
|-----------|-----------------|
|**Duración**|Agrupa las pruebas por tiempo de ejecución: **Rápido**, **Medio**y **Lento**.|
|**Resultado**|Agrupa las pruebas por resultados de ejecución: **Pruebas no superadas**, **Pruebas omitidas**y **Pruebas superadas**.|
|**Rasgos**|Agrupa las pruebas por los pares categoría-valor definidos. La sintaxis para especificar los valores y las categorías de rasgo se define desde el marco de pruebas unitarias.|
|**Proyecto**|Agrupa las pruebas por el nombre de los proyectos.|

### <a name="group-by-traits"></a>Agrupar por rasgos

 Por lo general, un rasgo es un par nombre-valor de categoría, pero también puede ser una sola categoría. Los rasgos se pueden asignar a los métodos identificados como métodos de prueba desde el marco de pruebas unitarias. Un marco de pruebas unitarias puede definir categorías de rasgo. Si lo desea, puede agregar valores a las categorías de rasgo para definir sus propios pares nombre-valor de categoría. La sintaxis para especificar los valores y las categorías de rasgo se define desde el marco de pruebas unitarias.

 **Rasgos del marco de pruebas unitarias de Microsoft para código administrado**

 En el marco de pruebas unitarias de Microsoft para aplicaciones administradas, el par nombre-valor de rasgo se define en un atributo  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> . El marco de pruebas también contiene estos rasgos predefinidos:

|Rasgo|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|La categoría de propietario se define desde el marco de pruebas unitarias y requiere un valor de cadena del propietario.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|La categoría de prioridad se define desde el marco de pruebas unitarias y requiere un valor entero de la prioridad.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|El atributo TestCategory permite proporcionar una categoría sin ningún valor. Las categorías que define el atributo TestCategory también pueden ser categorías del atributo TestProperty.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|El atributo TestProperty permite definir un par categoría-valor de rasgo.|

 **Rasgos del marco de pruebas unitarias de Microsoft para C++** Vea [Cómo usar el marco de pruebas unitarias de Microsoft para C++](how-to-use-microsoft-test-framework-for-cpp.md).

### <a name="search-and-filter-the-test-list"></a>Buscar y filtrar la lista de pruebas

Puede limitar los métodos de prueba en los proyectos que vea y ejecute con los filtros del Explorador de pruebas.

Si escribe una cadena en el cuadro de búsqueda del Explorador de pruebas y elige ENTRAR, la lista de pruebas se filtrará para mostrar solo las pruebas cuyos nombres completos contengan dicha cadena.

Para filtrar por otros criterios:

1. Abra la lista desplegable situada a la derecha del cuadro de búsqueda.

2. Elija un criterio nuevo.

3. Escriba el valor de filtro entre comillas.

![Filtrar pruebas en el Explorador de pruebas](../test/media/ute_filtertestlist.png "UTE_FilterTestList")

> [!NOTE]
> Las búsquedas distinguen entre mayúsculas y minúsculas, y coinciden con la cadena especificada en cualquier parte del valor de criterios.

|Calificador:|Description|
|---------------|-----------------|
|**Rasgo**|Busca coincidencias en el valor y en la categoría de rasgo. La sintaxis para especificar los valores y las categorías de rasgo se define en el marco de pruebas unitarias.|
|**Proyecto**|Busca coincidencias en los nombres de proyecto de prueba.|
|**Mensaje de error**|Busca coincidencias en los mensajes de error definidos por el usuario que devuelven las aserciones con errores.|
|**Ruta de acceso del archivo**|Busca coincidencias en el nombre de archivo completo de los archivos de origen de prueba.|
|**Nombre completo**|Busca coincidencias en el nombre de archivo completo de los métodos, las clases y los espacios de nombres de prueba.|
|**Salida**|Busca en los mensajes de error definidos por el usuario que se escriben en los resultados estándar (stdout) o en los errores estándar (stderr). La sintaxis para especificar los mensajes de salida se define en el marco de pruebas unitarias.|
|**Resultado**|Busca coincidencias en los nombres de categoría del Explorador de pruebas: **Pruebas no superadas**, **Pruebas omitidas**y **Pruebas superadas**.|

Puede excluir un subconjunto de resultados de un filtro con la sintaxis siguiente:

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Por ejemplo, `FullName:"MyClass" - FullName:"PerfTest"` devuelve todas las pruebas que incluyen "MyClass" en el nombre, excepto las que también incluyan "PerfTest".

## <a name="create-custom-playlists"></a>Crear listas de reproducción personalizadas

 Puede crear y guardar una lista de pruebas que desea ejecutar o ver como grupo. Al seleccionar una lista de reproducción, las pruebas de la lista aparecerán en el Explorador de pruebas. Si lo desea, puede agregar una prueba a varias listas de reproducción. Para acceder a todas las pruebas de un proyecto, elija la lista de reproducción predeterminada **Todas las pruebas** .

 ![Elegir una lista de reproducción](../test/media/ute_playlist.png "UTE_Playlist")

 **Para crear una lista de reproducción**, elija una o varias pruebas en el Explorador de pruebas. En el menú contextual, elija **Agregar a lista de reproducción**y **Nueva lista de reproducción**. Guarde el archivo con la ubicación y el nombre especificados en el cuadro de diálogo **Crear nueva lista de reproducción** .

 **Para agregar pruebas a una lista de reproducción**, elija una o varias pruebas en el Explorador de pruebas. En el menú contextual, elija **Agregar a lista de reproducción**y la lista de reproducción a la que desea agregar las pruebas.

 **Para abrir una lista de reproducción**, elija Prueba y Lista de reproducción en el menú de Visual Studio, y seleccione un elemento entre las listas de reproducción usadas recientemente. O bien, elija Abrir lista de reproducción para especificar el nombre y la ubicación de la lista de reproducción específica.

 Si las pruebas individuales no tienen ninguna dependencia que impida que se ejecuten en cualquier orden, active la ejecución de pruebas paralelas con el botón de alternancia ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png "UTE_parallelicon-small") en la barra de herramientas. Esto puede reducir considerablemente el tiempo necesario para ejecutar todas las pruebas.

## <a name="debug-and-analyze-unit-tests"></a>Depurar y analizar pruebas unitarias

### <a name="debug-unit-tests"></a>Depurar pruebas unitarias

Se puede usar el Explorador de pruebas para iniciar una sesión de depuración para las pruebas. La ejecución paso a paso del código con el depurador de Visual Studio permite avanzar y retroceder sin problemas entre las pruebas unitarias y el proyecto objeto de prueba. Para iniciar la depuración:

1. En el editor de Visual Studio, establezca un punto de interrupción en uno o varios métodos de prueba que desee depurar.

    > [!NOTE]
    > Dado que los métodos de prueba se pueden ejecutar en cualquier orden, establezca puntos de interrupción en todos los métodos de prueba que desee depurar.

2. En el Explorador de pruebas, seleccione los métodos de prueba y elija **Depurar pruebas seleccionadas** en el menú contextual.

 Para obtener más información sobre el depurador, vea [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md).

### <a name="diagnose-test-method-performance-issues"></a>Diagnosticar problemas de rendimiento del método de prueba

 Para diagnosticar por qué tarda demasiado un método de prueba, seleccione dicho método en el Explorador de pruebas y elija Perfil en el menú contextual. Vea [Explorador de rendimiento](../profiling/performance-explorer.md).

### <a name="analyze-unit-test-code-coverage"></a>Analizar la cobertura de código de prueba unitaria

Con la herramienta de cobertura de código de Visual Studio se puede determinar la cantidad del código de producto que las pruebas unitarias están probando realmente. La cobertura de código se puede ejecutar en pruebas seleccionadas o en todas las pruebas de una solución.

Para ejecutar la cobertura de código en los métodos de prueba de una solución:

1. Elija **Pruebas** en el menú de Visual Studio y seleccione **Analizar cobertura de código**.

2. En el submenú, elija uno de los comandos siguientes:

    - **Pruebas seleccionadas** ejecuta los métodos de prueba que ha seleccionado en el Explorador de pruebas.

    - **Todas las pruebas** ejecuta todos los métodos de prueba en la solución.

La ventana Resultados de la cobertura de código muestra el porcentaje de bloques de código de producto que se han ejecutado por línea, función, clase, espacio de nombres y módulo.

Para obtener más información, consulte [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Métodos abreviados de pruebas

Las pruebas se pueden ejecutar desde el **Explorador de pruebas**, haciendo clic con el botón derecho en una prueba del editor de código y seleccionando **Ejecutar prueba**, o mediante los [métodos abreviados del explorador de pruebas](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) predeterminados en Visual Studio. Algunos de los métodos abreviados dependen del contexto. Esto significa que ejecutan o depuran las pruebas en función de la posición del cursor en el editor de código. Si el cursor está dentro de un método de prueba, se ejecuta ese método de prueba. Si el cursor está en el nivel de clase, se ejecutan todas las pruebas de esa clase. Lo mismo sucede en el nivel de espacio de nombres.

|Comandos más frecuentes| Métodos abreviados de teclado|
|--------------|------------------------|
|TestExplorer.DebugAllTestsInContext|Ctrl+R, Ctrl+T|
|TestExplorer.RunAllTestsInContext|Ctrl+R, T|

> [!NOTE]
> No se puede ejecutar una prueba en una clase abstracta, ya que las pruebas solo se definen en las clases abstractas, no se crean instancias. Para ejecutar pruebas en las clases abstractas, cree una clase que se derive de la clase abstracta.

## <a name="see-also"></a>Vea también

- [Haga una prueba unitaria de su código](../test/unit-test-your-code.md)
- [Ejecutar una prueba unitaria como un proceso de 64 bits](../test/run-a-unit-test-as-a-64-bit-process.md)
