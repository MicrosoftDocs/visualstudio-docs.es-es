---
title: Usar la leyenda de la vista Diagramas para analizar pruebas de carga en Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Load Test Analyzer, graphs view legend
- load tests, graphs view legend
ms.assetid: 0f6ba8e4-1343-419c-8a9f-240cf50efed7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 967cc1c854689ba034077d25f61cea74d1f082a2
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="using-the-graphs-view-legend-to-analyze-load-tests"></a>Usar la leyenda de la vista Diagramas para analizar pruebas de carga

La vista Gráficos del Analizador de prueba de carga incluye un panel de leyenda con información sobre cada contador de rendimiento asociado al gráfico seleccionado.

![Leyenda de la vista Gráficos](../test/media/load_viewlegend.png "Load_ViewLegend")

La siguiente información se incluye en la leyenda:

-   **Mostrar en gráfico:** use las casillas para especificar si la línea de un contador determinado, como **Carga del usuario** o **Errores por segundo**, se traza en el gráfico. Active una casilla si desea trazar la línea en el gráfico. Desactive una casilla para quitar la línea del gráfico. Cuando se quita una línea del trazado, las estadísticas del contador continúan mostrándose en la leyenda.

-   **Intervalo:** esta columna muestra el intervalo del eje Y del contador de rendimiento. De forma predeterminada, este valor se ajustará automáticamente cuando cambie el intervalo de los datos de ejemplo. Un intervalo ajustado automáticamente siempre será la potencia siguiente de 10 mayor que el valor máx; incluye potencias negativas de diez. Un gráfico puede contener varios contadores, cada uno con un intervalo diferente. Por consiguiente, el eje Y no se etiqueta con un intervalo concreto, sino que se etiqueta con valores de 0-100 que representan un porcentaje del intervalo total de cada contador. Por ejemplo, para un contador con un intervalo de 1000, un punto de datos de 60 en el eje Y corresponde a un valor de 600 del contador.

    > [!NOTE]
    > Puede desactivar el ajuste del valor del rango automático bloqueando el intervalo en un valor concreto. Cuando se bloquea el intervalo, los valores que superen el intervalo se muestran como el valor máximo que especificó en la parte superior del gráfico. Use el cuadro de diálogo **Opciones de trazado** para bloquear el intervalo en un valor concreto. Para obtener más información, vea [Cómo: Especificar opciones de trazado para contadores de gráficos](../test/how-to-specify-plot-options-for-graphing-counters.md).

-   **Contador:** las cuatro columnas denominadas **Contador**, **Instancia**, **Categoría** y **Equipo** identifican el contador de rendimiento de manera única.

-   **Color:** la columna **Color** muestra el color y el estilo de la línea trazada para el contador de rendimiento. Use el cuadro de diálogo **Opciones de trazado** para cambiar el color o el estilo de línea de un contador de rendimiento en el gráfico. El cuadro de diálogo **Opciones de trazado** está disponible en el menú contextual de la leyenda. Para obtener más información, vea [Cómo: Especificar opciones de trazado para contadores de gráficos](../test/how-to-specify-plot-options-for-graphing-counters.md).

-   **Estadísticas:** las columnas **Mín**, **Máx**, **Pro** y **Último** muestran las estadísticas respectivas del contador de rendimiento. Estos valores corresponden a los datos que se muestran en el área visible del gráfico. Por ejemplo, si hace zoom en el área de una ejecución, las estadísticas de la leyenda solo reflejarán los valores de esa área. La columna "Último" es el valor del contador de rendimiento en el último intervalo de muestreo completado.

    > [!NOTE]
    > La columna Último solo se muestra en el leyenda del Analizador de prueba de carga mientras la prueba se está ejecutando.

     Para obtener más información, vea [Cómo: Acercar una región del gráfico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

La selección de un elemento de la leyenda hace lo siguiente:

-   Permite quitar el elemento de la leyenda y el gráfico. Presione la tecla **Supr** o haga clic con el botón derecho en el elemento y seleccione **Eliminar**.

-   Resalta la línea trazada en el gráfico.

-   Hace que la cuadrícula de datos muestre los datos del elemento seleccionado.

-   Permite acceder al cuadro de diálogo **Opciones de trazado** del contador.

> [!TIP]
> Puede usar el botón desplegable **Opciones del gráfico** de la barra de herramientas del Analizador de pruebas de carga y seleccionar **Mostrar leyenda** para mostrar u ocultar el panel **Leyenda** asociado a la vista de gráfico.

## <a name="see-also"></a>Vea también

- [Cómo: Especificar opciones de trazado para contadores de gráficos](../test/how-to-specify-plot-options-for-graphing-counters.md)
- [Cómo: Acercar una región del gráfico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md)
- [Analizar los resultados de pruebas de carga en la vista Gráficos](../test/analyze-load-test-results-in-the-graphs-view.md)