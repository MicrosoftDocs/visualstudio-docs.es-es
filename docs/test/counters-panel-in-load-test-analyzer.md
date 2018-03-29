---
title: Panel Contadores para analizar pruebas de carga en Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, counters panel
ms.assetid: e1a388d7-5d33-4631-931a-5653ac4aefdc
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 9e693872784519f5cdcacbd0691b6f69334af22e
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="use-the-counters-panel-in-graphs-view-and-tables-view"></a>Usar el panel Contadores en la vista Gráficos y la vista Tablas

El panel Contadores es visible en la vista Gráficos y en la vista Tablas del Analizador de prueba de carga mientras se está ejecutando una prueba de carga o cuando está analizando el resultado de una prueba de carga. Para obtener más información, vea [Analizar los resultados de pruebas de carga en la vista Gráficos](../test/analyze-load-test-results-in-the-graphs-view.md), [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) y [Cómo: Obtener acceso a los resultados de pruebas de carga para su análisis](../test/how-to-access-load-test-results-for-analysis.md).

El panel de contadores muestra una vista estructurada de los contadores de rendimiento recopilados durante la prueba de carga. Puede mostrar u ocultar el panel de contadores si elige **Mostrar panel de contadores** en la barra de herramientas del Analizador de pruebas de carga.

Los contadores se organizan en una estructura de árbol donde los nodos son instancias del contador de rendimiento que se pueden trazar en un gráfico.

El panel Contadores proporciona las siguientes características:

-   Comunica información sobre infracciones de umbral.

-   Selección de contadores para gráficos.

-   Una vista de árbol estructurada de todos los contadores de rendimiento recopilados durante una ejecución de pruebas de carga con las siguientes ramas principales:

    -   **Conjunto:** contiene el resumen de datos del contador de rendimiento para cada agente de prueba y para la prueba de carga completa.

    -   **Nombre de escenario:** las bifurcaciones etiquetadas con nombres de escenario de prueba de carga en el árbol de contadores de rendimiento contienen todas las instancias de contador de prueba de carga asociadas a un escenario de prueba de carga determinado. La mayoría de los contadores de prueba de carga están anidados dentro de una birfurcación del escenario.

         Una bifurcación de escenario contiene nodos de pruebas de rendimiento web. Los nodos de pruebas de rendimiento web contienen los nodos Páginas, Solicitudes y Transacción. Cualquier nodo de esta estructura es un contador de rendimiento que se puede agregar a un gráfico.

    -   **Equipos:** contienen todas las instancias del contador de pruebas de no carga agrupadas por equipo. La bifurcación Equipos contiene un nodo por equipo asociado al controlador de prueba de carga especificado en la sección Roles de la configuración de pruebas seleccionada actualmente. Para obtener más información, vea [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md).

         Cada nodo de equipo contiene un conjunto de categorías de contador de rendimiento recopiladas de ese equipo. Las categorías contienen contadores y los contadores contienen nombres de instancia del contador de rendimiento.

    -   **Errores:** contiene todos los errores detectados durante la prueba de carga. El nodo Errores contiene varios nodos de error de subcategoría. Las subcategorías son específicas de diferentes tipos de error como, por ejemplo, las excepciones y los errores HTTP.

### <a name="scenario-name-node-in-counters-panel"></a>Nodo Nombre de escenario del panel Contadores

|||
|-|-|
|![Nodo de nombre de escenario del panel Contadores](../test/media/ltest__namenode.png)|1. Todos los contadores de rendimiento asociados al Escenario1 de la prueba de carga aparecen bajo este nodo.<br />2. Todas las pruebas de un escenario se encuentran bajo el nodo de escenario. La etiqueta indica el nombre de la prueba.<br />3. Los nodos hoja bajo un nodo de prueba son los contadores de casos de prueba de carga donde el nombre de instancia del contador es el nombre de la prueba.<br />4. Todas las instancias de contador de páginas de prueba de carga asociadas a una bifurcación de prueba de rendimiento web. En este nodo, todas las instancias de contador de prueba de carga asociadas a la página GET del inicio de sesión (nombre de informe) de la prueba de rendimiento web IBuyBrowse del Escenario1 están aquí.<br />5. Los nodos bajo un nodo de página son los contadores de páginas de la prueba de carga.<br />6. Todas las instancias de contador de solicitudes de prueba de carga asociadas a una prueba de rendimiento web están dentro de una bifurcación de prueba de rendimiento web. En este nodo, todas las instancias de contador de solicitudes asociadas a la solicitud GET del inicio de sesión (nombre de informe) de la prueba de rendimiento web IBuyBrowse del Escenario1 o la prueba de carga están aquí.<br />7. Los nodos hoja bajo un nodo de solicitudes son los contadores de solicitudes de prueba de carga.<br />8. Todas las instancias de contador de transacciones de prueba de carga asociadas a una prueba de rendimiento web están dentro de una rama de prueba de rendimiento web. En este nodo, todas las instancias de contador de transacciones asociadas a la transacción denominada Transacción1 de la prueba de rendimiento web IBuyBrowse del Escenario1 de la prueba de carga están aquí.<br />9. Los nodos hoja bajo un nodo de transacciones son los contadores de transacciones de prueba de carga.<br />10. Nodo de prueba unitaria.|

## <a name="tasks"></a>Tareas

|Tareas|Temas relacionados|
|-----------|-----------------------|
|**Agregar más contadores de rendimiento a un gráfico en la vista de gráfico:** en el panel Contadores, puede agregar distintos tipos de datos a un gráfico de prueba de carga. Para ello, agregue más contadores de rendimiento al gráfico.|-   [Cómo: Agregar y eliminar contadores de los gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Analizar los umbrales especificados en la prueba de carga que se infringieron:** el panel Contadores muestra iconos que representan infracciones del umbral que después puede agregar a tablas y a gráficos para realizar un análisis más extenso.|-   [Cómo: Analizar las infracciones del umbral con el panel Contadores](../test/analyze-threshold-rule-violations-in-load-tests.md)|
|**Analizar los errores detectados durante la ejecución de pruebas de carga:** el panel Contadores incluye un nodo de errores que contiene categorías de error y subcategorías como errores de HTTP que puede usar para agregar errores a gráficos para realizar un análisis más extenso.|-   [Cómo: Analizar errores con el panel Contadores](../test/how-to-analyze-errors-using-the-counters-panel.md)|

## <a name="performance-counter-sampling-interval-considerations"></a>Consideraciones sobre el intervalo de muestreo de los contadores de rendimiento

Elija un valor para la propiedad **Frecuencia de muestreo** en los parámetros de ejecución de pruebas de carga según la duración de la prueba de carga. Una velocidad de muestra menor, como el valor predeterminado de cinco segundos, necesita más espacio en la base de datos de resultados de pruebas de carga. En el caso de pruebas de carga más largas, el incremento de la velocidad de muestra reduce la cantidad de datos recopilados. Para obtener más información, vea [Cómo: Especificar la frecuencia de muestreo](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

He aquí algunas instrucciones sobre las velocidades de muestra:

|Duración de la prueba de carga|Tasa del ejemplo recomendada|
|------------------------|-----------------------------|
|\< 1 hora|5 segundos|
|De 1 a 8 horas|15 segundos|
|De 8 a 24 horas|30 segundos|
|> 24 horas|60 segundos|

## <a name="considerations-for-including-timing-details-to-collect-percentile-data"></a>Consideraciones para incluir detalles de tiempo para recopilar datos de percentiles

Hay una propiedad en los parámetros de ejecución del Editor de pruebas de carga denominada **Almacenamiento de detalles de tiempo**. Si se habilita la propiedad **Almacenamiento de detalles de tiempo**, el tiempo que tarda en ejecutarse cada prueba, cada transacción y cada página durante la prueba de carga se almacenará en el repositorio de resultados de pruebas de carga. De este modo, se pueden mostrar datos como percentiles 90 y 95 en el Analizador de prueba de carga en las tablas Pruebas, Transacciones y Páginas.

Hay dos opciones para habilitar la propiedad **Almacenamiento de detalles de tiempo** en las propiedades de los parámetros de ejecución: **Solo estadísticas** y **Todos los detalles individuales**. Con cualquier opción, se cronometran todas las pruebas, páginas y transacciones individuales y se calculan los datos como percentiles a partir de los datos de tiempo individuales. La diferencia es que con la opción **Solo estadísticas**, en cuanto se han calculado los datos de percentiles, los datos de tiempo individuales se eliminan del repositorio. Esto reduce la cantidad de espacio necesario en el repositorio cuando se usan detalles de tiempo. Sin embargo, los usuarios avanzados pueden procesar los datos de detalle de tiempo de otras formas mediante herramientas de SQL. En tal caso, se debe usar la opción **Todos los detalles individuales** para que los datos de detalles de tiempo estén disponibles para ese procesamiento. Además, si establece la propiedad en **Todos los detalles individuales**, puede analizar la actividad del usuario virtual mediante el Diagrama de actividad del usuario virtual del Analizador de pruebas de carga una vez que finaliza la ejecución de la prueba de carga. Para obtener más información, vea [Analizar la actividad de usuario virtual en la vista Detalles](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

La cantidad de espacio necesario en el repositorio de resultados de pruebas de carga para almacenar los detalles de tiempo podría ser grande, sobre todo si se trata de pruebas de carga de ejecución prolongada. Además, se tarda más tiempo en almacenar estos datos en dicho repositorio al final de la prueba de carga, puesto que los datos se almacenan en los agentes de prueba de carga hasta que finaliza la ejecución. Cuando la prueba de carga termina, los datos se almacenan en el repositorio. De forma predeterminada, la propiedad **Almacenamiento de detalles de tiempo** está habilitada. Si esto supone algún problema para el entorno de pruebas, puede establecer **Almacenamiento de detalles de tiempo** en **Ninguno**.

Para obtener más información, vea [Cómo: Especificar la propiedad Almacenamiento de detalles de tiempo](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="see-also"></a>Vea también

- [Analizar resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)