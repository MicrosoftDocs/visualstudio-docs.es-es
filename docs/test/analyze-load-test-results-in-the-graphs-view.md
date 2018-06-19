---
title: Analizar los resultados de pruebas de carga en la vista Gráficos del Analizador de prueba de carga
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graph.view
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, graphs in Load Test Viewer
- Load Test Viewer, graphs
- load tests, results graphs
- load tests, using graphs
- load test results, graphs
ms.assetid: 4a919cd8-541c-40ee-be3b-352fabc56140
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 5540eb31d764e82cb0c6cd46eb63cb893559a70f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973159"
---
# <a name="analyze-load-test-results-in-the-graphs-view-of-the-load-test-analyzer"></a>Analizar los resultados de pruebas de carga en la vista Gráficos del Analizador de pruebas de carga

Los resultados de una prueba de carga se muestran como datos en varios paneles diferentes.

Para mostrar los resultados de las pruebas como gráficos, elija **Gráficos** en la barra de herramientas de la prueba de carga. Cada uno de los gráficos se muestra en un panel con el nombre del gráfico mostrado en la parte superior en una lista desplegable. Para mostrar un gráfico diferente en el panel, elija un nombre de gráfico diferente en la lista.

Se pueden mostrar hasta cuatro paneles de gráficos a la vez. Puede alternar entre los distintos diseños de panel utilizando el botón de la barra de herramientas de diseño de panel.

Se proporcionan varios gráficos integrados. Puede utilizar estos gráficos integrados tal cual o puede personalizarlos. Además, puede crear sus propios gráficos. Para obtener más información, vea [Cómo: Agregar y eliminar contadores de los gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md) y [Cómo: Crear gráficos personalizados](../test/how-to-create-custom-graphs-in-load-test-results.md).

## <a name="built-in-graphs"></a>Gráficos integrados

En la tabla siguiente se muestran los gráficos integrados disponibles para analizar resultados de pruebas de carga.

|Nombre del gráfico|Description|
|----------------|-----------------|
|Indicadores clave|Contadores que describen aspectos básicos del rendimiento de la prueba, como carga del usuario, rendimiento y tiempo de respuesta.|
|Tiempo de respuesta de la prueba|Datos sobre el tiempo que tardan las pruebas en ejecutarse.|
|Tiempo de respuesta de la página|Tiempo medio de respuesta de las páginas web a las que se tiene acceso durante la prueba de carga.|
|Sistema a prueba|Información sobre los equipos en los que se ejecuta la aplicación que se está probando. Incluye datos sobre el uso de memoria, el procesador, el disco físico y los procesos.<br /><br /> De forma predeterminada, sólo se recopilan datos de los contadores Mbytes disponibles y Tiempo de procesador.|
|Controlador y agentes|Información sobre los equipos en los que se ejecutan las pruebas de carga. Incluye datos sobre el uso de memoria, el procesador, el disco físico y los procesos.<br /><br /> De forma predeterminada, sólo se recopilan datos de los contadores Mbytes disponibles y Tiempo de procesador.|
|Tiempo de respuesta de la transacción|Tiempo medio de respuesta de las transacciones realizadas en la prueba de carga.|

 Puede mostrar diferentes contadores en el gráfico, tanto en tiempo de ejecución como después de la ejecución de una prueba.

> [!NOTE]
> Sólo se pueden agregar contadores de rendimiento de tiempo de respuesta a un gráfico de tiempo de respuesta generado automáticamente.

 La información del contador se muestra en el gráfico y en la leyenda situada debajo de los gráficos. También puede acercar con el zoom una sección del gráfico. Para obtener más información, vea [Cómo: Acercar una región del gráfico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

## <a name="counters-displayed-in-graphs"></a>Contadores mostrados en gráficos

 En los gráficos se muestran *contadores*. Los contadores hacen referencia a los datos recopilados durante una prueba de carga, como las pruebas realizadas por segundo o el tiempo medio de la prueba. Para obtener más información sobre los contadores, vea [Especificar los conjuntos de contadores y las reglas de umbral para equipos en una prueba de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

 En la leyenda de los contadores que se muestran en los gráficos aparecen varias columnas de datos útiles sobre la ejecución de la prueba de carga. Para desactivar la presentación de cualquier dato en el gráfico, desactive la casilla situada en la fila de la leyenda.

 La leyenda contiene las columnas siguientes:

|Contador|El nombre del contador|
|-------------|-----------------------------|
|Instancia|El nombre de la instancia del contador.|
|Categoría|El nombre de la categoría del contador.|
|Equipo|Nombre del equipo en el que se recopilan datos del contador.|
|Color|El color de la línea del gráfico.|
|Intervalo|Indica el número que representa el 100 en el gráfico para ese contador. Por ejemplo, para un intervalo cuyo valor superior es 10.000, la etiqueta 100 situada en la parte superior del gráfico representa 10.000.|
|Mín.|Indica el valor mínimo del contador en milisegundos.|
|Max|Indica el valor máximo del contador en milisegundos.|
|Avg.|Indica el valor medio del contador en milisegundos.|
|Último|Muestra el valor del contador durante el intervalo de muestreo más reciente en milisegundos.|

## <a name="tasks"></a>Tareas

|Tareas|Temas relacionados|
|-----------|-----------------------|
|**Personalizar los gráficos mediante la leyenda:** la leyenda de la vista Gráficos muestra información de cada contador de rendimiento asociado a un gráfico. Puede utilizar la leyenda para quitar los contadores de rendimiento, resaltarlos en el gráfico y personalizar las opciones de trazado.|-   [Usar la leyenda de la vista Diagramas para analizar pruebas de carga](../test/use-the-graphs-view-legend-to-analyze-load-tests.md)|
|**Mostrar contadores en los gráficos:** puede agregar diferentes tipos de datos a un gráfico de resultados de pruebas de carga si coloca contadores en el gráfico.|-   [Cómo: Agregar y eliminar contadores de los gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Acercar gráficos:** una vez terminada una prueba de carga, puede usar las barras de zoom para acercar una región del gráfico y desplazarse por ella. Al aplicar el zoom para acercar, puede examinar los datos que se generaron durante la ejecución de una prueba de carga con más detalle.|-   [Cómo: Acercar una región del gráfico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)|
|**Mostrar gráficos en mosaico:** puede organizar los gráficos de resultados de pruebas de carga de varias formas. Puede colocar en mosaico hasta cuatro gráficos.||
|**Modificar el aspecto de los trazados de los contadores de rendimiento en los gráficos:** puede cambiar las opciones de líneas de trazado de los contadores de rendimiento en los gráficos. Esto incluye el color y el estilo de línea. Además, puede especificar el intervalo que va a utilizar para trazar el contador de rendimiento automática o manualmente.|-   [Cómo: Especificar opciones de trazado para contadores de gráficos](../test/how-to-specify-plot-options-for-graphing-counters.md)|
|**Crear gráficos personalizados:** puede diseñar gráficos que muestren información específica sobre los resultados de pruebas de carga. Los gráficos personalizados se diseñan especificando los contadores de la prueba de carga que se van a mostrar en el gráfico.|-   [Cómo: Crear gráficos personalizados](../test/how-to-create-custom-graphs-in-load-test-results.md)|
|**Exportar los datos de los contadores de rendimiento del gráfico:** puede exportar los datos del gráfico a Microsoft Excel con el botón Exportar datos de gráfico a Excel de la barra de herramientas Analizador de pruebas de carga mientras está en la vista Gráficos.||

## <a name="related-tasks"></a>Tareas relacionadas

 [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)

 [Cómo: Obtener acceso a los resultados de pruebas de carga para su análisis](../test/how-to-access-load-test-results-for-analysis.md)

 [Analizar resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

## <a name="see-also"></a>Vea también

- [Cómo: Agregar y eliminar contadores de los gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
- [Cómo: Crear gráficos personalizados](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Cómo: Acercar una región del gráfico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)