---
title: Análisis de la actividad de usuario virtual de prueba de carga en Visual Studio
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: c91cd1a2ea721743c289b6664ddd0a76ceedbc4f
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750843"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analizar la actividad de usuario virtual de prueba de carga en la vista Detalles del Analizador de prueba de carga

**Diagrama de actividad del usuario virtual**

 ![Diagrama de actividad del usuario virtual](../test/media/virtual_actchart.png)

 La vista Detalles muestra el Diagrama de actividad de usuarios virtuales, que se utiliza para analizar lo que hicieron los usuarios virtuales durante la prueba de carga. El gráfico de actividad de los usuarios virtuales permite ver los modelos de actividad de los usuarios y modelos de carga, relacionar las pruebas con errores o lentas, y ver solicitudes con otra actividad de usuario virtual. El Diagrama de actividad del usuario virtual también puede ayudar a determinar los picos máximos en el uso de la CPU, las caídas de solicitudes por segundo, y qué pruebas o páginas se estaban ejecutando durante esos momentos de máxima y mínima actividad.

> [!NOTE]
> Antes de ejecutar la prueba de carga para la que desea utilizar el Gráfico de detalles de actividad de usuarios virtuales, debe comprobar que la propiedad **Almacenamiento de detalles de tiempo** está establecida en la opción **Todos los detalles individuales** utilizando el Editor de pruebas de carga de rendimiento. Para obtener más información, vea [Cómo: Configurar los resultados de pruebas para recopilar información completa para habilitar la actividad de usuario virtual en los resultados de pruebas](../test/how-to-configure-load-tests-to-collect-full-details.md).

 **Panel Leyenda de detalles**

 ![Panel Leyenda de detalles](../test/media/ltest_detailslegend.png)

 El panel Leyenda de detalles está visible en el Diagrama de actividad del usuario virtual. El panel de leyenda de detalles permite filtrar las pruebas, las páginas y las transacciones según criterios diferentes. Por ejemplo, puede quitar ciertas pruebas de la vista o quitar todas las pruebas superadas, o bien quitar las pruebas no superadas en las que se produjeron determinados errores. También puede quitar todas las pruebas que no tienen registros.

 Puede resaltar las pruebas no superadas de modo que todas se muestren de color rojo. También puede resaltar las pruebas que tengan registros de prueba. Las pruebas con registros se colorearán en verde.

 **Panel Resultados del filtro**

 ![Panel Resultados del filtro](../test/media/ltest_filterresults.png)

 El panel Resultados del filtro está visible en el Diagrama de actividad del usuario virtual. El panel Resultados del filtro puede filtrar por lo siguiente:

-   **Mostrar solo resultados con registros** Muestra únicamente los resultados de pruebas que tienen registros de prueba asociados.

-   **Mostrar resultados correctos** Muestra los resultados correctos.

-   **Mostrar resultados con errores** Muestra los resultados con errores que pueden ayudar en la depuración.

## <a name="tasks"></a>Tareas

|Tareas|Temas relacionados|
|-----------|-----------------------|
|**Configurar la prueba de carga para utilizar el Diagrama de actividad del usuario virtual:** antes de ejecutar una prueba de carga en la que desea ver los datos de actividad de los usuarios virtuales, debe configurar los valores de las propiedades de las pruebas de carga.|-   [Cómo: Configurar la recopilación de información completa para habilitar el Diagrama de actividad del usuario virtual](../test/how-to-configure-load-tests-to-collect-full-details.md)|
|**Ejecutar una prueba de carga:** una vez creada y configurada una prueba de carga para habilitar la recopilación de datos de actividad de los usuarios virtuales, debe ejecutar la prueba hasta el final para ver el diagrama de actividad del usuario virtual.||
|**Ver los resultados de pruebas de carga que contienen los datos de actividad de los usuarios virtuales:** una vez creada, configurada y completada una prueba de carga, puede ver los datos de actividad de los usuarios virtuales en el diagrama de actividad del usuario virtual.|-   [Analizar resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Cómo: Analizar lo que hacen los usuarios virtuales durante una prueba de carga](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Aislar los problemas de rendimiento en las pruebas de carga:** puede utilizar el Diagrama de actividad del usuario virtual como ayuda para aislar los problemas de rendimiento en la prueba de carga.|-   [Tutorial: Usar el Diagrama de actividad del usuario virtual para aislar problemas de rendimiento](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Vea también

- [Analizar resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)