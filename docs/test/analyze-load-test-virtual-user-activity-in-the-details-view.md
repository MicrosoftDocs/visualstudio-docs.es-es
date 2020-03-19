---
title: Analizar la actividad de usuario virtual de prueba de carga
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0289ff0d4a20eacc4f6801d9300d39df594bc79e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591240"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Análisis de la actividad de usuario virtual de prueba de carga en la vista Detalles del Analizador de pruebas de carga

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Diagrama de actividad del usuario virtual**

![Diagrama de actividad del usuario virtual](../test/media/virtual_actchart.png)

La vista **Detalles** muestra el **Diagrama de actividad del usuario virtual**, que se usa para analizar visualmente lo que hicieron los usuarios virtuales durante la prueba de carga. El **Diagrama de actividad del usuario virtual** permite ver los modelos de actividad de los usuarios y los modelos de carga, poner en correlación las pruebas con errores o lentas, y ver solicitudes con otra actividad de usuario virtual. El **Diagrama de actividad del usuario virtual** también puede ayudar a determinar los picos máximos en el uso de la CPU, las caídas de solicitudes por segundo, y qué pruebas o páginas se estaban ejecutando durante esos momentos de máxima y mínima actividad.

> [!NOTE]
> Antes de ejecutar la prueba de carga para la que quiere utilizar el **Diagrama de actividad del usuario virtual**, debe comprobar que la propiedad **Almacenamiento de detalles de tiempo** está establecida en la opción **AllIndividualDetails** mediante el Editor de pruebas de carga de rendimiento.

**Panel Leyenda de detalles**

![Panel Leyenda de detalles](../test/media/ltest_detailslegend.png)

El panel de leyenda de detalles está visible en el **Diagrama de actividad del usuario virtual**. El panel de leyenda de detalles permite filtrar las pruebas, las páginas y las transacciones según criterios diferentes. Por ejemplo, puede quitar ciertas pruebas de la vista o quitar todas las pruebas superadas, o bien quitar las pruebas no superadas en las que se produjeron determinados errores. También puede quitar todas las pruebas que no tienen registros.

Puede resaltar las pruebas no superadas de modo que todas se muestren de color rojo. También puede resaltar las pruebas que tengan registros de prueba. Las pruebas con registros se colorearán en verde.

**Panel Resultados del filtro**

![Panel Resultados del filtro](../test/media/ltest_filterresults.png)

El panel Resultados del filtro está visible en el **Diagrama de actividad del usuario virtual**. El panel Resultados del filtro puede filtrar por lo siguiente:

- **Mostrar solo resultados con registros** Muestra únicamente los resultados de pruebas que tienen registros de prueba asociados.

- **Mostrar resultados correctos** Muestra los resultados correctos.

- **Mostrar resultados con errores** Muestra los resultados con errores que pueden ayudar en la depuración.

## <a name="tasks"></a>Tareas

|Tareas|Temas relacionados|
|-|-|
|**Ejecutar una prueba de carga:** una vez creada y configurada una prueba de carga para habilitar la recopilación de datos de actividad del usuario virtual, debe ejecutar la prueba hasta el final para ver el **Diagrama de actividad del usuario virtual**.||
|**Ver los resultados de pruebas de carga que contienen los datos de actividad del usuario virtual:** una vez creada, configurada y completada una prueba de carga, puede ver los datos de actividad del usuario virtual en el **Diagrama de actividad del usuario virtual**.|-   [Analizar los resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Cómo: Analizar lo que hacen los usuarios virtuales durante una prueba de carga](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Aislar los problemas de rendimiento en las pruebas de carga:** puede usar el **Diagrama de actividad del usuario virtual** como ayuda para aislar los problemas de rendimiento en la prueba de carga.|-   [Tutorial: Usar el Diagrama de actividad del usuario virtual para aislar problemas de rendimiento](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Vea también

- [Analizar los resultados de pruebas de carga con el analizador de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
