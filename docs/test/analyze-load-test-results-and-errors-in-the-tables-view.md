---
title: Análisis de los errores y resultados de las pruebas de carga
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.pageresult
- vs.test.load.dialog.column
- vs.test.load.monitor.requestresult
- vs.test.load.monitor.testresult
- vs.test.load.monitor.table.view
- vs.test.load.monitor.agentresult
- vs.test.load.monitor.transactionresult
helpviewer_keywords:
- tables, Load Test Viewer options
- load test results, tables
- load tests, Load Test Viewer
- data [Visual Studio ALM], load test tables
- Load Test Viewer, tables
- load tests, results tables
ms.assetid: 0a84bda3-6051-45eb-9c7f-d57419e1f97d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 98e54e8e1bec7502e7401dc6a13a639e92c1a881
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823046"
---
# <a name="analyze-load-test-results-and-errors-in-the-tables-view-of-the-load-test-analyzer"></a>Analizar los errores y resultados de pruebas de carga en la vista Tablas del Analizador de pruebas de carga

Al ver los resultados de una ejecución de pruebas de carga, puede abrir paneles diferentes que proporcionan distintas maneras de analizar los datos. Puede ver los datos en forma de gráfico, ver cómo cambian con el tiempo o ver los datos en forma de tablas detalladas.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Para cambiar a la vista de tablas, elija **Tablas** en la barra de herramientas de la **prueba de carga**. Para cambiar entre las distintas tablas, use la lista desplegable **Tablas** en la barra de herramientas situada encima de la cuadrícula de la tabla. En la vista de tabla, puede ver hasta cuatro tablas a la vez. Para más información, vea [Disponer en mosaico tablas de pruebas de carga](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#tile-load-test-tables) en este tema.

La mayoría de los valores numéricos mostrados en una tabla para los contadores de rendimiento son acumulativos a lo largo de toda la ejecución de la prueba de carga. Las columnas denominadas **En último lugar** son una excepción y representan el valor del intervalo de muestreo más reciente.

> [!NOTE]
> Las columnas denominadas **En último lugar** solo están disponibles mientras se ejecuta una prueba de carga. Una vez finalizada la prueba de carga, estas columnas no están disponibles.

Para ordenar la mayoría de las tablas, puede elegir el título de la columna según la que desea ordenar. De forma predeterminada, algunas tablas no muestran todas las columnas disponibles. Puede agregar columnas a las tablas, si hay columnas disponibles. Para agregar columnas, haga clic con el botón derecho en la tabla y elija **Agregar o quitar columnas**.

> [!NOTE]
> Puede copiar los datos de una tabla en otras aplicaciones, como Excel, para ulteriores análisis.

## <a name="the-load-test-tables"></a>Las tablas de prueba de carga

La tabla siguiente muestra las tablas que están disponibles para analizar ejecuciones de prueba de carga.

|Nombre de la tabla|Descripción|
|-|-|
|Errores|Muestra una lista de errores producidos durante la ejecución de la prueba de carga. Para obtener más información, vea la [tabla Errores](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-errors-table) en este tema, así como [Analizar resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|
|Páginas|Muestra una lista de páginas a las que se obtiene acceso durante la ejecución de una prueba de carga. Algunos datos de esta tabla sólo están disponibles después de que finalice una prueba de carga. Para obtener más información, vea [Cómo: Ver la respuesta de las páginas web](../test/how-to-view-web-page-response-time-in-a-load-test.md).|
|Solicitudes|Muestra los detalles para las solicitudes individuales emitidas durante una prueba de carga. Esto incluye todas las solicitudes HTTP y solicitudes dependientes tales como imágenes. Para obtener más información, vea la [tabla Solicitudes](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-requests-table) en este tema.|
|Seguimiento SQL|Muestra los resultados de una traza SQL. Esta tabla sólo está disponible después de que finalice una prueba de carga y sólo si se utiliza la traza SQL durante la prueba. Para obtener más información, vea la [tabla de datos Seguimiento de SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table) en este tema.|
|Pruebas|Muestra los detalles para las pruebas individuales ejecutadas durante una prueba de carga. Para obtener más información, vea la [tabla Pruebas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-tests-table) en este tema.|
|Umbrales|Muestra una lista de infracciones a las reglas de umbral producidas durante la ejecución de la prueba de carga. Para obtener más información, vea [Analizar las infracciones de las reglas de umbral](../test/analyze-threshold-rule-violations-in-load-tests.md).|
|Transacciones|Muestra una lista de transacciones producidas durante la ejecución de una prueba de carga. Para obtener más información, vea la [tabla Transacciones](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-transactions-table) en este tema.|
|Agentes|Solo muestra si la prueba de carga usa agentes de prueba y controlador de prueba. Muestra una lista de los agentes que se utilizaron durante la ejecución de la prueba de carga. La tabla Agentes incluye la cantidad de solicitudes que el agente ha probado y, de todas ellas, las que han dado error. Asimismo incluye el número de pruebas de la combinación que el agente probó y cuántas dieron error.|
|Detalles de las pruebas|Muestra los detalles de las pruebas incluidas en la combinación de pruebas para la prueba de carga. Los detalles incluyen el nombre de la prueba, el escenario en el que se ejecutó, cuándo se inició, el tiempo que llevó la ejecución y el resultado que indica si la prueba fue correcta o dio error. Si la prueba dio error, se muestra un vínculo en la columna **Detalles**. Puede elegir el vínculo para ir al Editor de prueba de rendimiento web, donde la solicitud que dio error aparece resaltada.|

## <a name="collect-percentile-data"></a>Recopilar datos de percentil

 Algunas tablas de prueba de carga pueden contener columnas adicionales, que incluyen datos de percentil y tiempos de respuesta divididos en grupos basados en una emulación de red. De forma predeterminada, estos datos no se recopilan. Los datos de percentiles solo están disponibles al guardar los resultados en una base de datos, no cuando se guardan de forma local. Para obtener más información, vea [Administrar resultados de pruebas de carga en el repositorio de resultados de pruebas de carga](../test/manage-load-test-results-in-the-load-test-results-repository.md). Además, para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución específico que quiera cambiar. En la ventana **Propiedades**, para la propiedad **Almacenamiento de detalles de tiempo**, seleccione **StatisticsOnly** o **AllIndividualDetails**. Para obtener más información, vea [Cómo: Ver la respuesta de las páginas web](../test/how-to-view-web-page-response-time-in-a-load-test.md).

## <a name="the-requests-table"></a>La tabla Solicitudes

 La tabla **Solicitudes** muestra los detalles para las solicitudes individuales emitidas durante una prueba de carga. Esto incluye todas las solicitudes HTTP y solicitudes dependientes tales como imágenes. La tabla muestra las solicitudes por prueba y escenario, porque una solicitud puede estar incluida en muchas pruebas y escenarios.

 La tabla siguiente muestra las columnas de la tabla **Solicitudes**:

|Columna|Descripción|Visible de forma predeterminada|
|-|-|-|
|**Solicitud**|Dirección URL de la solicitud. Por ejemplo, *home.html* u *orange-arrow.gif*.|Sí|
|**Escenario**|El nombre del escenario.|Sí|
|**Prueba**|Nombre de la prueba.|Sí|
|**Total**|Número total de veces que se ha emitido esta solicitud de prueba de rendimiento web durante la ejecución de pruebas de carga. El total incluye las solicitudes superadas y no superadas pero no las solicitudes almacenadas en la memoria caché, porque no se emiten al servidor web.|Sí|
|**Superado**|Número de veces que se ha emitido y pasado la solicitud.|No|
|**Con error**|Número de veces con la solicitud emitida y fallida. Las entradas de esta columna aparecen como hipervínculos. Puede elegir cualquier hipervínculo para ver una lista de los errores individuales en el cuadro de diálogo **Errores de prueba de carga**. Para obtener más información, vea [Analizar los resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Sí|
|**En caché**|Número total de veces que se ha almacenado la solicitud en la memoria caché.|No|
|**Solicitudes por segundo**|Tasa de la solicitud por segundo durante la ejecución de la prueba de carga.|No|
|**Pasadas por segundo**|Tasa de esta solicitud por segundo durante la ejecución de la prueba de carga, para las instancias pasadas de esta solicitud.|No|
|**Errores por segundo**|Tasa de esta solicitud por segundo durante la ejecución de la prueba de carga, para las instancias fallidas de esta solicitud.|No|
|**Tiempo hasta el primer byte**|Tiempo medio para recibir el primer byte de la respuesta, medido desde la hora a la que se envió la solicitud al servidor web. Las unidades son segundos.|No|
|**Tiempo de respuesta**|Tiempo medio para recibir la respuesta completa a una solicitud, medido desde la hora a la que se envió la solicitud al servidor web. Las unidades son segundos.|Sí|
|**Longitud del contenido**|Longitud media del contenido de la respuesta a la solicitud. Las unidades son bytes.|Sí|

## <a name="the-tests-table"></a>La tabla Pruebas

 La tabla **Pruebas** muestra los detalles para las pruebas individuales ejecutadas durante una prueba de carga. La tabla muestra las pruebas por prueba y escenario, porque una prueba puede estar incluida en muchos escenarios.

 La tabla siguiente muestra las columnas de la tabla **Pruebas**.

|Columna|Descripción|Visible de forma predeterminada|
|-|-|-|
|**Prueba**|Nombre de la prueba.|Sí|
|**Escenario**|El nombre del escenario.|Sí|
|**Total**|Número total de veces que se ejecutó la prueba en el escenario. Esto incluye el número de veces con la solicitud pasada y fallida.|Sí|
|**Superado**|Número de veces que se ejecutó y pasó la prueba en el escenario.|Sí|
|**Con error**|Número de veces que se ejecutó y fue fallida la prueba en el escenario. Las entradas de esta columna aparecen como hipervínculos. Puede elegir cualquier hipervínculo para ver una lista de los errores individuales en el cuadro de diálogo **Errores de prueba de carga**. Para obtener más información, vea [Analizar los resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md).|Sí|
|**Pruebas por segundo**|Tasa de la prueba por segundo durante la ejecución de la prueba de carga.|Sí|
|**Pasadas por segundo**|Tasa de esta prueba por segundo durante la ejecución de la prueba de carga, para las instancias pasadas de esta solicitud.|No|
|**Errores por segundo**|Tasa de esta prueba por segundo durante la ejecución de la prueba de carga, para las instancias fallidas de esta solicitud.|No|
|**Tiempo de la prueba**|Tiempo medio para ejecutar la prueba durante la ejecución de la prueba de carga. Las unidades son segundos.|Sí|
|**90 % del tiempo de la prueba**|El 90º valor de percentil para el tiempo de prueba.|No|
|**95 % del tiempo de la prueba**|El 95º valor de percentil para el tiempo de prueba.|Sí|
|**Solicitudes por prueba**|Número medio de solicitudes de la prueba si se trata de una prueba de rendimiento web.|No|

## <a name="the-transactions-table"></a>La tabla Transacciones

 La tabla **Transacciones** muestra una lista de las transacciones producidas durante la ejecución de una prueba de carga. Las transacciones hacen referencia a cualquier transacción definida en una prueba de rendimiento web o a los temporizadores definidos en una prueba unitaria. La transacción no hace referencia a las transacciones de la base de datos.

 La tabla siguiente muestra las columnas de la tabla **Transacciones**.

> [!NOTE]
> Para ver todas las columnas, debe habilitar la propiedad Almacenamiento de detalles de tiempo con los parámetros de ejecución activos. Para obtener más información, vea [Cómo: Especificar la propiedad Almacenamiento de detalles de tiempo](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

|Columna|Descripción|Visible sin detalles de tiempo|
|-|-|-|
|**Transacción**|Nombre de la transacción.|Sí|
|**Escenario**|El nombre del escenario.|Sí|
|**Prueba**|Nombre de la prueba.|Sí|
|**Total**|Número total de transacciones emitidas durante la ejecución de la prueba de carga.|Sí|
|**Tiempo de la transacción**|Tiempo de ejecución de la transacción de una prueba de carga. Para las pruebas de rendimiento web, el tiempo de reflexión está incluido en el cálculo. Las unidades son segundos.|No|
|**Tiempo de respuesta**|Tiempo de respuesta de la transacción de prueba de rendimiento web en la ejecución de una prueba de carga. El tiempo de respuesta se diferencia del tiempo de transacción en que el tiempo de respuesta no incluye ningún tiempo de reflexión ocurrido durante la transacción. Las unidades son segundos.|No|
|**Tiempo medio de transacción**|Tiempo medio de la transacción. Incluye los tiempos de reflexión. Por ejemplo, si hay tres solicitudes cada una con un tiempo de reflexión, incluirá los tiempos de reflexión y el tiempo real de ejecución de las solicitudes.|No|
|**Tiempo medio de respuesta**|Tiempo de respuesta medio de una transacción de la prueba de rendimiento web en la ejecución de una prueba de carga. El tiempo de respuesta se diferencia del tiempo de transacción en que el tiempo de respuesta no incluye ningún tiempo de reflexión ocurrido durante la transacción. Las unidades son segundos.|No|
|**Tiempo de respuesta mín.**|No incluye los tiempos de reflexión.|No|
|**Tiempo de respuesta máx.**|No incluye los tiempos de reflexión.|No|
|**Mediana de tiempo de respuesta**|No incluye los tiempos de reflexión.|No|
|**Tiempo de respuesta al 90 %**|El 90º valor de percentil para el tiempo de transacción. No incluye los tiempos de reflexión. **Nota:**  Esto es diferente de Visual Studio Team System 2008 Test Load Agent, donde se usaba el valor **90 % del tiempo de transacción**.|No|
|**Tiempo de respuesta al 95 %**|El 95º valor de percentil para el tiempo de transacción. No incluye los tiempos de reflexión. **Nota:**  Esto es diferente de Visual Studio Team System 2008 Test Load Agent, donde se usaba el valor **95 % del tiempo de transacción**.|No|
|**Tiempo de respuesta al 99 %**|Valor de percentil 99º para el tiempo de transacción. No incluye los tiempos de reflexión.|No|
|**Desv. est. de tiempo de respuesta**|No incluye los tiempos de reflexión.|No|

## <a name="the-errors-table"></a>La tabla Errores

 Al ejecutar una prueba de carga, puede analizar los errores que se producen. Analizar los errores y ajustar las pruebas son una parte importante del proceso de las pruebas de carga. Si se producen errores, aparece un hipervínculo de **errores** en la barra de estado de la prueba de carga y especifica el número de errores que se produjeron. Para mostrar la tabla de errores, elija el hipervínculo.

 La tabla de errores agrupa los errores que se produjeron durante una prueba de carga por tipo y subtipo de error. También existe una línea **total** en la tabla que especifica el recuento total de todos los errores que se produjeron.

 La tabla de errores contiene las columnas siguientes:

|Columna|Descripción|Visible de forma predeterminada|
|-|-|-|
|Tipo|Tipo del error. Por ejemplo, HttpError.|Sí|
|Subtipo|Subtipo del error. Por ejemplo, LoadTestException.|Sí|
|Recuento|Número de errores de este tipo que se produjeron durante la prueba de carga. Las entradas de esta columna aparecen como hipervínculos. Puede elegir cualquier hipervínculo para ver una lista de errores individuales.|Sí|
|Último mensaje|Mensaje que describe el error. Por ejemplo, 404 - NotFound.|Sí|

 Para obtener más información, vea [Trabajar con tablas de pruebas de carga](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

### <a name="drill-down-to-the-error-list"></a>Explorar en profundidad la lista de errores

La tabla de errores agrupa los errores por tipo y subtipo de error. Para ver una tabla de los errores individuales, abra el cuadro de diálogo **Errores de prueba de carga**. Para ello, elija un hipervínculo en la columna **Recuento** de la tabla de errores. También puede mostrarlo si hace clic con el botón derecho en una fila de la tabla de errores rellenada y elige **Errores**.

> [!NOTE]
> Se recopilan sólo las primeras 1.000 repeticiones de cualquier tipo y combinación de subtipos de errores. Al abrir el cuadro de diálogo **Errores de prueba de carga**, verá como máximo las primeras 1.000 repeticiones de ese error.

La tabla **Errores de prueba de carga** contiene las columnas siguientes:

|Columna|Descripción|
|-|-|
|**Tiempo**|Hora durante la prueba de carga en la que se produjo el error.|
|**Agent**|Nombre del equipo agente en el que se produjo el error. Esto es importante al ejecutar pruebas de carga usando controladores de pruebas y agentes de prueba. Para obtener más información, vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).|
|**Prueba**|Nombre de la prueba de rendimiento web en la se produjo el error.|
|**Escenario**|Nombre del escenario en el que se produjo el error.|
|**Solicitud**|Dirección URL de la solicitud en la que se produjo el error.|
|**Type**|Tipo del error. Por ejemplo, HttpError.|
|**Subtipo**|Subtipo del error. Por ejemplo, LoadTestException.|
|**Texto**|Texto del mensaje de error. Por ejemplo, 404 - NotFound.|
|**Pila**|Las entradas de esta columna están vacías o la palabra **Pila** tiene formato de hipervínculo. Puede elegir el hipervínculo para ver un seguimiento de la pila del error.|
|**Detalles**|Las entradas de esta columna están vacías o la palabra **TestLog** tiene formato de hipervínculo. Este vínculo puede ayudarle a aislar errores en la prueba de carga. Por ejemplo, al elegir el vínculo **TestLog** en un error de solicitud de una prueba de rendimiento web, se abrirán los resultados de la prueba de rendimiento web en el Visor de resultados de pruebas de rendimiento web y se resaltará el error de solicitud.|

> [!NOTE]
> Puede ordenar la tabla eligiendo los encabezados de columna.

## <a name="the-sql-trace-data-table"></a>Tabla de datos Seguimiento de SQL

Puede recopilar información de seguimiento SQL durante la ejecución de una prueba de carga y realizar el análisis más tarde. La recopilación de datos de seguimiento permite identificar las consultas y los procedimientos almacenados que se ejecutan más despacio en la base de datos de SQL Server que se está probando.

Cuando se habilita la traza SQL, se crea un archivo durante la ejecución de la prueba de carga que contiene la información de seguimiento. Al final de la ejecución de prueba, estos datos se guardan automáticamente en el Almacén de resultados de pruebas de carga y se elimina el archivo de seguimiento. Analice la información de seguimiento en la tabla **Seguimiento SQL** después de que se haya completado la prueba de carga.

### <a name="to-view-sql-trace-data"></a>Para ver los datos de seguimiento SQL

1. En el Analizador de pruebas de carga, elija **Tablas** en la barra de herramientas para asegurarse de que se muestra la cuadrícula de la tabla.

2. En el cuadro de lista desplegable **Tabla**, seleccione **Seguimiento SQL**.

3. Los datos de seguimiento recopilados durante la ejecución se muestran en la cuadrícula. La tabla muestra las operaciones SQL que se ejecutan más lentamente, ordenadas por duración, con la más lenta al principio. Normalmente, la columna **Duración**es la primera que se examina. Los datos se muestran en milisegundos.

   Se muestran las siguientes columnas:

    - **Clase de evento**

    - **Duración**

    - **CPU**

    - **Lecturas**

    - **Escrituras**

    - **TextData**

    - **StartTime**

    - **EndTime**

   Si desea realizar el seguimiento de eventos SQL distintos de los datos identificados en estas columnas, puede configurar su propia traza de SQL personalizada mediante SQL Server Profiler, una herramienta que es independiente de Visual Studio.

## <a name="tile-load-test-tables"></a>Disponer en mosaico tablas de pruebas de carga

Cuando se ven los resultados de una ejecución de pruebas de carga, puede ver los datos como tablas detalladas. Para cambiar a la vista de tablas, elija **Tablas** en la barra de herramientas de la **prueba de carga**. Las tablas que están disponibles son **Errores**, **Páginas**, **Solicitudes**, **Seguimiento SQL**, **Pruebas**, **Umbrales** y **Transacciones**. Para obtener más información, vea [Trabajar con tablas de pruebas de carga](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

En la vista de tabla, puede ver a la vez hasta cuatro tablas sin que se superpongan.

### <a name="to-tile-tables"></a>Para colocar tablas en mosaico

1. En la barra de herramientas del **Analizador de pruebas de carga**, elija **Tablas**.

     Se abre la vista de tabla. El diseño predeterminado consiste en dos paneles horizontales.

2. En la barra de herramientas del **Analizador de prueba de carga**, haga clic en el botón de **diseño** y, luego, elija una de las opciones siguientes:

    - **Un panel**

    - **Dos paneles horizontales**

    - **Tres paneles horizontales**

    - **Cuatro paneles horizontales**

3. Para alternar entre las distintas tablas, utilice la lista desplegable situada encima de la cuadrícula de la tabla en cada panel.

    > [!NOTE]
    > No puede mostrar la misma tabla en más de un panel. Si cambia la tabla mostrada en un panel a una ya mostrada en otro panel, las tablas intercambian los paneles.

## <a name="see-also"></a>Vea también

- [Analizar los resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Cómo: Acceder a los resultados de pruebas de carga para el análisis](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizar los resultados de pruebas de carga en la vista Gráficos](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analizar las infracciones de las reglas de umbral](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Administrar resultados de pruebas de carga en el repositorio de resultados de pruebas de carga](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Información general de resumen de resultados de pruebas de carga](../test/load-test-results-summary-overview.md)