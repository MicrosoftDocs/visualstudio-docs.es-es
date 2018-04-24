---
title: Analizar los resultados de pruebas de carga en Visual Studio | Microsoft Docs
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test results
- load tests, analyzing test results
- load tests, managing test results
ms.assetid: 8a4ba300-425d-447c-91d9-c53f4345feee
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 7add3789d3c48fb405818f50efd47bb83cb9f899
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="analyze-load-test-results-using-the-load-test-analyzer"></a>Analizar los resultados de pruebas de carga con el Analizador de pruebas de carga

Busque cuellos de botella, identifique errores y mida las mejoras de su aplicación cuando use el Analizador de prueba de carga . Analice los resultados de pruebas de carga de estas formas:

-   Supervisar una prueba de carga cuando se está ejecutando.

-   Analizar una prueba de carga finalizada.

-   Ver los resultados de una prueba de carga anterior.

También puede crear informes que comparen dos o más informes de análisis de tendencias para compartirlos con las partes interesadas. Vea [Informar de los resultados de las pruebas de carga para las comparaciones de pruebas o los análisis de tendencias](../test/compare-load-test-results.md).

Puede completar estas tareas tanto si ejecuta la prueba de carga desde Visual Studio Enterprise o desde la línea de comandos, y tanto si la ejecuta en un solo equipo como en una máquina remota.

## <a name="differences-between-analyzing-a-running-and-a-completed-load-test"></a>Diferencias entre el análisis de una prueba de carga en ejecución y una completada

 Al ejecutar una prueba de carga, el Analizador de pruebas de carga se muestra en una pestaña independiente, junto con el nombre de la prueba de carga y la hora a la que se inició la prueba (por ejemplo, **PruebaCarga1 [12:40 p.m.]**). Cuando se ejecuta una prueba de carga, se mantiene en la memoria un conjunto más reducido de los datos de contadores de rendimiento. Puede supervisar este conjunto de datos cuando se ejecuta la prueba de carga. Al término de la prueba de carga, puede analizar el conjunto de datos completo de la base de datos. Hay diferencias en cuanto a los datos que se muestran cuando se ejecuta una prueba de carga y los datos que puede ver después de que se haya completado una prueba de carga. Por ejemplo, los datos de tiempo de respuesta del 90 y el 95 por ciento no se calculan hasta que la prueba de carga se ha completado. También hay algunas diferencias en la funcionalidad de las herramientas disponibles para analizar los datos.

 Al ejecutar la prueba de carga, hay dos vistas disponibles: la vista Gráficos y la vista Tablas. La vista Gráficos le permite representar mediante gráficos los contadores de rendimiento que se recopilan. La vista Tablas ofrece información sobre cada una de las pruebas, páginas, transacciones y solicitudes que se recopilan. También obtiene una tabla que enumera los errores.

 De forma predeterminada, cuando la ejecución de la prueba de carga se ha completado, se muestra la vista Resumen. Puede cambiar entre las vistas Resumen, Gráficos, Tablas y Detalles mediante la barra de herramientas. El Analizador de pruebas de carga se puede acoplar o dejar que flote usando las técnicas habituales de manipulación de ventanas de Visual Studio. Al analizar ejecuciones de pruebas de carga completadas, puede tener abiertos varios analizadores de prueba de carga al mismo tiempo para comparar diferentes ejecuciones de pruebas de carga.

## <a name="tasks"></a>Tareas

|Tareas|Temas relacionados|
|-----------|-----------------------|
|**Obtener acceso a los resultados de su prueba de carga:** cuando se ejecuta una prueba de carga desde el Editor de pruebas de carga, los resultados de pruebas de carga se abren automáticamente y la prueba de carga en ejecución se muestra en el Analizador de pruebas de carga.|-   [Cómo: Obtener acceso a los resultados de pruebas de carga para su análisis](../test/how-to-access-load-test-results-for-analysis.md)|
|**Agregar notas de análisis a su prueba de carga:** puede agregar comentarios a la prueba de carga al realizar el análisis. Los comentarios se almacenan de forma permanente, junto con el resultado de la prueba de carga. La descripción que escriba también aparecerá en la columna **Descripción** asociada a la prueba de carga en el cuadro de diálogo Abrir y administrar resultados de pruebas en el Editor de pruebas de carga.<br /><br /> Para obtener más información, consulte [Cómo: Tener acceso a los resultados de pruebas de carga para su análisis](../test/how-to-access-load-test-results-for-analysis.md).<br /><br /> Además, los comentarios se muestran al crear un informe de Excel para los resultados de pruebas de carga.<br /><br /> Para obtener más información, consulte [Informar de los resultados de las pruebas de carga para las comparaciones de pruebas o los análisis de tendencias](../test/compare-load-test-results.md).|-   [Cómo: Agregar comentarios mientras se analiza una prueba de carga completada](../test/how-to-add-comments-on-a-completed-load-test.md)|
|**Analizar los resultados de una prueba de carga:** después de tener acceso a los datos de ejecución de pruebas de carga, puede analizar los resultados. Puede ver el resumen de la prueba de carga para conocer rápidamente los resultados. El resumen de la prueba de carga muestra los resultados clave en un formato compacto y fácil de leer.<br /><br /> Puede imprimir el resumen de la prueba de carga. Resulta cómodo para utilizarlo cuando deba comunicar los resultados a los interesados.<br /><br /> Puede analizar los detalles de los resultados de pruebas de carga usando los gráficos y las tablas de los resultados. Esto incluye Errores, Páginas, Solicitudes, Seguimiento SQL, Pruebas, Umbrales y Transacciones.|-   [Información general de resumen de resultados de pruebas de carga](../test/load-test-results-summary-overview.md)<br />-   [Cómo: Ver la respuesta de las páginas web](../test/how-to-view-web-page-response-time-in-a-load-test.md)<br />-   [Analizar las infracciones de las reglas de umbral](../test/analyze-threshold-rule-violations-in-load-tests.md)<br />-   [Analizar los resultados de pruebas de carga en la vista Gráficos](../test/analyze-load-test-results-in-the-graphs-view.md)<br />-   [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)|
|**Analizar la actividad de los usuarios virtuales en los resultados de pruebas de carga para aislar problemas de rendimiento:** puede utilizar el Diagrama de actividad del usuario virtual para visualizar lo que hacen los usuarios virtuales durante una prueba de carga. Esto puede ayudarle a aislar los picos en el uso de la CPU o la reducción del número de solicitudes por segundo, y determinar qué pruebas o páginas se están ejecutando durante esos períodos de actividad máxima y mínima.|-   [Analizar la actividad de usuario virtual en la vista Detalles](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)|