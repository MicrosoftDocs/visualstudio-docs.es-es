---
title: Adición y eliminación de contadores de los gráficos de resultados de pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 21fa28e9ff149bcf117e3bde5d553a2cf641c04a
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896528"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Cómo: Agregar y eliminar contadores de los gráficos de resultados de pruebas de carga

Puede usar el panel **Contadores** para agregar contadores de rendimiento a un gráfico.

![Contador agregado a un gráfico](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Consideraciones sobre el intervalo de muestreo de los contadores de rendimiento**

Elija un valor para la propiedad **Frecuencia de muestreo** en los parámetros de ejecución de pruebas de carga según la duración de la prueba de carga. Una velocidad de muestra menor, como el valor predeterminado de cinco segundos, necesita más espacio en la base de datos de resultados de pruebas de carga. En el caso de pruebas de carga más largas, el incremento de la velocidad de muestra reduce la cantidad de datos recopilados. Para más información, vea [Cómo: Especificar la velocidad de muestra de los parámetros de ejecución de pruebas de carga](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

He aquí algunas instrucciones sobre las velocidades de muestra:

|Duración de la prueba de carga|Tasa del ejemplo recomendada|
|-|-----------------------------|
|\< 1 hora|5 segundos|
|De 1 a 8 horas|15 segundos|
|De 8 a 24 horas|30 segundos|
|> 24 horas|60 segundos|

**Consideraciones para incluir detalles de tiempo para recopilar datos de percentiles**

Hay una propiedad en los parámetros de ejecución del Editor de pruebas de carga denominada **Almacenamiento de detalles de tiempo**. Si la propiedad **Almacenamiento de detalles de tiempo** está habilitada, se almacena el tiempo que tarda en ejecutarse cada prueba, transacción y página individual durante la prueba de carga en el repositorio de resultados de pruebas de carga. De este modo, se pueden mostrar datos como percentiles 90 y 95 en el **Analizador de pruebas de carga** en las tablas Pruebas, Transacciones y Páginas.

Hay dos opciones para habilitar la propiedad **Almacenamiento de detalles de tiempo** en las propiedades de los parámetros de ejecución: **Solo estadísticas** y **Todos los detalles individuales**. Con cualquier opción, se cronometran todas las pruebas, páginas y transacciones individuales y se calculan los datos como percentiles a partir de los datos de tiempo individuales. La diferencia es que con la opción **Solo estadísticas**, en cuanto se han calculado los datos de percentiles, los datos de tiempo individuales se eliminan del repositorio. Esto reduce la cantidad de espacio necesario en el repositorio cuando se usan detalles de tiempo. Sin embargo, los usuarios avanzados pueden procesar los datos de detalle de tiempo de otras formas mediante herramientas de SQL. En tal caso, se debe usar la opción **Todos los detalles individuales** para que los datos de detalles de tiempo estén disponibles para ese procesamiento. Además, si establece la propiedad en **AllIndividualDetails**, puede analizar la actividad de los usuarios virtuales mediante el **diagrama de actividad del usuario virtual** del **Analizador de pruebas de carga** una vez que se completa la ejecución de la prueba de carga. Para obtener más información, vea [Analizar la actividad de usuario virtual de prueba de carga en la vista Detalles del Analizador de prueba de carga](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

La cantidad de espacio necesario en el repositorio de resultados de pruebas de carga para almacenar los detalles de tiempo podría ser muy grande, sobre todo si se trata de pruebas de carga de ejecución prolongada. Además, se tarda más tiempo en almacenar estos datos en dicho repositorio al final de la prueba de carga, puesto que los datos se almacenan en los agentes de prueba de carga hasta que finaliza la ejecución. Cuando la prueba de carga termina, los datos se almacenan en el repositorio. De forma predeterminada, la propiedad **Almacenamiento de detalles de tiempo** está habilitada. Si esto supone algún problema para el entorno de pruebas, puede establecer **Almacenamiento de detalles de tiempo** en **Ninguno**.

Para más información, vea [Cómo: Especificar la propiedad Almacenamiento de detalles de tiempo para el parámetro de ejecución de una prueba de carga](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Para mostrar un contador determinado en un gráfico de prueba de carga

1.  Una vez finalizada la carga de una prueba, o después de cargar el resultado de una prueba, en la barra de herramientas del Analizador de pruebas de carga, elija **Gráficos**.

     El panel **Contadores** aparece en la vista Gráficos.

    > [!NOTE]
    > Si el panel **Contadores** no está visible, elija **Mostrar panel de contadores** en la barra de herramientas.

2.  En el panel **Contadores**, expanda los nodos de la jerarquía hasta que encuentre el contador de rendimiento que desea ver mostrado gráficamente.

     Por ejemplo, para mostrar la memoria disponible en el equipo en el que se ejecutan las pruebas, expanda **Equipos**, expanda el nodo del equipo y, luego, expanda **Memoria**. Verá el contador **MB disponibles**.

3.  Elija el gráfico para el que desea mostrar el contador de rendimiento.

4.  Haga clic con el botón derecho en el contador de rendimiento en el panel **Contadores** y seleccione **Mostrar contador en el gráfico**.

    > [!TIP]
    > Para dejar de mostrar temporalmente los datos del contador de rendimiento en el gráfico, desactive la casilla correspondiente al contador de rendimiento en la leyenda. Esto permite seguir analizando las estadísticas mínima, máxima y promedio sin ver la línea de tendencia en el gráfico. Esto puede ser útil si el gráfico contiene trazados de varios contadores de rendimiento que se superponen mientras está analizando problemas. Para más información, consulte [Usar la leyenda de la vista Diagramas para analizar pruebas de carga](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5.  Para quitar los datos del contador de rendimiento del gráfico, haga clic con el botón derecho en el contador de rendimiento en la columna **Contador** de la leyenda y seleccione **Eliminar**.

     \- o -

     Haga clic con el botón derecho en la línea de datos del gráfico y seleccione **Eliminar**.

     \- o -

     Elija el contador de rendimiento en la columna **Contador** de la leyenda o en la línea de datos del gráfico y, luego, presione la tecla **Supr**.

    > [!NOTE]
    > También puede colocar un contador de rendimiento en la leyenda, pero no en el gráfico con el comando **Agregar contador en la leyenda**.

## <a name="see-also"></a>Vea también

- [Analizar los resultados de pruebas de carga en la vista Gráficos](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Cómo: Crear gráficos personalizados](../test/how-to-create-custom-graphs-in-load-test-results.md)