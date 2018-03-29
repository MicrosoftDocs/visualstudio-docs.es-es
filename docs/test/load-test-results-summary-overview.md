---
title: Información general de resumen de resultados de pruebas de carga en Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
f1_keywords:
- vs.test.load.monitor.summary.view
helpviewer_keywords:
- load test results, summary
- load tests, summary in analyzer
- load tests, results summary
- Load Test Viewer, summary
- load tests, summary in Load Test Viewer
ms.assetid: 326b6c3c-5378-452b-8ca3-ba5a06ab3d41
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 6222e5288526dd5806997b8b65f326e841b692af
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="load-test-results-summary-overview"></a>Información general de resumen de resultados de pruebas de carga

Después de ejecutar una prueba de carga, puede ver el resumen para entender rápidamente los resultados. El resumen de la prueba de carga proporciona los resultados clave en un formato compacto y fácil leer. También puede imprimir el resumen de la prueba de carga. Resulta cómodo para utilizarlo cuando deba comunicar los resultados a los interesados. El resumen de la prueba de carga también es la vista predeterminada cuando se abre un resultado de prueba de carga de una prueba ejecutada previamente. Para obtener más información, consulte [Cómo: Tener acceso a los resultados de pruebas de carga para su análisis](../test/how-to-access-load-test-results-for-analysis.md).

 ![Vista de resumen](../test/media/ltest_summaryview.png "LTest_SummaryView")

## <a name="the-load-test-summary"></a>Resumen de la prueba de carga

El resumen de la prueba de carga está dividido en secciones. Las secciones iniciales aparecen en la parte superior del resumen y siempre están visibles. Al ver el resumen de la prueba de carga, los elementos siguientes aparecen en primer lugar:

- Información de serie de pruebas

- Resultados globales

- Estadística clave: Las 5 páginas más lentas

- Estadística clave: Las 5 pruebas más lentas

- Estadística clave: Las 5 operaciones SQL más lentas

    > [!NOTE]
    > La sección de operaciones SQL únicamente se muestra si está habilitada la traza de SQL en la prueba de carga.

Las secciones de cierre aparecen al final del resumen y se pueden contraer para ahorrar espacio. Los elementos siguientes aparecen al final del resumen de la prueba de carga:

- Resultados de pruebas

- Resultados de la página

- Resultados de la transacción

- Recursos del sistema sometido a prueba

- Recursos de controlador y agentes

- Errores

## <a name="test-run-information"></a>Información de serie de pruebas

La sección de información de ejecución de prueba contiene información general sobre la ejecución, incluidos el nombre de la prueba, las horas de inicio y finalización, y el controlador que ha ejecutado la prueba. Esta sección también contiene la descripción opcional de la ejecución que se agrega al ejecutar la prueba de carga.

## <a name="overall-results"></a>Resultados globales

La sección de resultados globales contiene resultados resumidos de la prueba, incluidos el número de solicitudes, el número total de solicitudes no superadas, el tiempo medio de respuesta y el promedio de tiempo de página.

## <a name="key-statistic-top-5-slowest-pages"></a>Estadística clave: Las 5 páginas más lentas

La sección de páginas más lentas contiene las 5 páginas más lentas de la prueba de carga. Para cada página, se muestran la dirección URL y el tiempo medio de carga de la página. Las páginas se muestran en orden descendente. Puede elegir la dirección URL de una página para abrir la tabla **Páginas** e inspeccionar más detalles de esa página. Para más información, vea [Cómo: Ver el tiempo de respuesta de la página web](../test/how-to-view-web-page-response-time-in-a-load-test.md).

El valor de percentil para **95 % del tiempo de página (seg.)** informa de que 95 % de las páginas completaron en menos tiempo en segundos.

## <a name="key-statistic-top-5-slowest-tests"></a>Estadística clave: Las 5 pruebas más lentas

La sección de pruebas más lentas contiene las 5 pruebas más lentas de la prueba de carga. Para cada prueba, se muestran el nombre de la prueba y el tiempo medio de prueba. Las pruebas se muestran en orden descendente. Puede elegir el nombre de una prueba para abrir la tabla **Pruebas** e inspeccionar más detalles de esa prueba. Para obtener más información, vea [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

El valor de percentil para **95 % del tiempo de la prueba (seg.)** informa de que 95 % de las páginas se completaron en menos tiempo en segundos.

## <a name="key-statistic-top-5-slowest-sql-operations"></a>Estadística clave: Las 5 operaciones SQL más lentas

Si la traza de SQL está habilitada en la prueba de carga, la sección de consultas más lentas contiene las 5 consultas más lentas de la prueba de carga. Para cada prueba se muestra el nombre de la operación y la duración. La duración se muestra en microsegundos (SQL Server 2005) o milisegundos (SQL Server 2000 y versiones anteriores). Las pruebas se muestran en orden descendente según su duración. Puede elegir el nombre de una operación para abrir la tabla **Seguimiento SQL** e inspeccionar más detalles de esa operación. Para más información, vea [la tabla de datos de seguimiento SQL](../test/analyze-load-test-results-and-errors-in-the-tables-view.md#the-sql-trace-data-table).

## <a name="test-results"></a>Resultados de pruebas

La sección de resultados de pruebas contiene una lista de todas las pruebas y todos los escenarios de la prueba de carga. Se muestran el nombre de la prueba, el escenario, el número de veces que se ejecutó, el número de veces que produjo un error y el tiempo medio de prueba. Puede elegir el nombre de una prueba para abrir la tabla **Pruebas** e inspeccionar más detalles de esa prueba. Para obtener más información, vea [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Puede expandir o contraer esta sección eligiendo la flecha situada a la izquierda del título de la sección.

## <a name="page-results"></a>Resultados de la página

La sección de resultados de página contiene una lista de todas las páginas web de la prueba de carga. Se muestran la dirección URL, el escenario, el nombre de la prueba, el tiempo medio de página y el recuento. Puede elegir la dirección URL de una página para abrir la tabla **Páginas** e inspeccionar más detalles de esa página. Para más información, vea [Cómo: Ver el tiempo de respuesta de la página web](../test/how-to-view-web-page-response-time-in-a-load-test.md).

> [!NOTE]
> Puede expandir o contraer esta sección eligiendo la flecha situada a la izquierda del título de la sección.

## <a name="transaction-results"></a>Resultados de la transacción

La sección de resultados de la transacción contiene una lista de todas las transacciones de la prueba de carga. Se muestran el nombre de la transacción, el escenario, la prueba, el tiempo de respuesta, el tiempo transcurrido y el recuento. Puede elegir el nombre de una transacción para abrir la tabla **Transacciones** e inspeccionar más detalles de esa transacción. Para obtener más información, vea [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

> [!NOTE]
> Puede expandir o contraer esta sección eligiendo la flecha situada a la izquierda del título de la sección.

Los valores de percentil notifican la siguiente información de la transacción:

-   El 90 % de las transacciones se completaron en menos de \<tiempo> segundos.

-   El 95 % de las transacciones se completaron en menos de \<tiempo> segundos.

## <a name="system-under-test-resources"></a>Recursos del sistema sometido a prueba

La sección de recursos del sistema sometido a prueba contiene una lista de equipos que son el conjunto de equipos de destino para los que se genera la carga. Incluye todos los equipos en los que se recolecten conjuntos de contadores que no sean el agente o el controlador. Se muestran el nombre del equipo, el porcentaje de tiempo de procesador y la memoria disponible. Puede elegir un nombre de equipo para abrir el gráfico **Sistema a prueba** y ver el uso de los recursos a lo largo del tiempo. Para obtener más información, vea [Analizar los resultados de pruebas de carga en la vista Gráficos del Analizador de pruebas de carga](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Puede expandir o contraer esta sección eligiendo la flecha situada a la izquierda del título de la sección.

## <a name="controller-and-agent-resources"></a>Recursos de controlador y agentes

La sección de recursos de controlador y agentes contiene una lista de equipos que se utilizan para ejecutar la prueba. Se muestran el nombre del equipo, el porcentaje de tiempo de procesador y la memoria disponible. Puede elegir un nombre de equipo para abrir el gráfico **Controlador y agentes** y ver el uso de los recursos a lo largo del tiempo. Para obtener más información, vea [Analizar los resultados de pruebas de carga en la vista Gráficos del Analizador de pruebas de carga](../test/analyze-load-test-results-in-the-graphs-view.md).

> [!NOTE]
> Puede expandir o contraer esta sección eligiendo la flecha situada a la izquierda del título de la sección.

## <a name="errors"></a>Errores

La sección de errores contiene una lista de todos los errores que se han producido durante la prueba de carga. Se muestran el tipo y subtipo del error, el recuento y el último mensaje. Puede elegir un error para abrir la tabla **Errores** e inspeccionar más detalles de ese error. Para obtener más información, vea [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) y [Cómo: Analizar errores con el panel Contadores](../test/how-to-analyze-errors-using-the-counters-panel.md).

> [!NOTE]
> Puede expandir o contraer esta sección eligiendo la flecha situada a la izquierda del título de la sección.

## <a name="printing-a-summary"></a>Imprimir un resumen

Puede imprimir el resumen de la prueba de carga eligiendo **Imprimir** en el menú contextual del resumen. Puede ver antes una vista previa de la impresión eligiendo **Vista previa de impresión** en el menú contextual del resumen. También puede imprimir directamente desde la pantalla de vista previa.

## <a name="see-also"></a>Vea también

- [Analizar las infracciones de las reglas de umbral](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analizar resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)