---
title: Análisis de los errores en las pruebas de carga con el Panel de contadores en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, counters panel
ms.assetid: 981b4f1e-505a-4078-a06d-58ae17d996b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: bc7beb1100b5e1bfe3fd554da53520ffc9888e64
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751889"
---
# <a name="how-to-analyze-errors-using-the-counters-panel"></a>Cómo: Analizar errores con el panel Contadores

El panel Contadores es visible en la vista Gráficos y en la vista Tablas del Analizador de prueba de carga mientras se está ejecutando una prueba de carga o cuando está analizando el resultado de una prueba de carga. Para obtener más información, vea [Analizar los resultados de pruebas de carga en la vista Gráficos](../test/analyze-load-test-results-in-the-graphs-view.md), [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) y [Cómo: Obtener acceso a los resultados de pruebas de carga para su análisis](../test/how-to-access-load-test-results-for-analysis.md).

 El nodo **Errores** del panel Contadores contiene todos los errores que se detectaron durante la prueba de carga. El nodo Errores contiene varios nodos de error de subcategoría que son específicos de los diferentes tipos de errores. Por ejemplo, **Excepciones** y **Errores HTTP**.

 ![Nodo de errores del panel Contadores](../test/media/ltest_errornode.png)

## <a name="to-analyze-errors-in-the-counters-panel"></a>Para analizar errores en el panel Contadores

1.  Después de que se complete una prueba de carga, o después de cargar el resultado de una prueba, en la barra de herramientas del Analizador de pruebas de carga, elija **Gráficos** o **Tablas**.

     El panel **Contadores** se mostrará en la vista Gráficos o en la vista Tablas.

2.  Si el panel Contadores no está visible, elija **Mostrar panel de contadores** en la barra de herramientas.

3.  Expanda el nodo **Errores** y seleccione una categoría de error o una subcategoría de error que desee analizar.

4.  Haga clic con el botón secundario en el error y seleccione una de las opciones siguientes:

    -   **Mostrar contador en el gráfico**: en la vista Gráficos, el error se agrega y resalta en el gráfico seleccionado. Para obtener más información, vea [Cómo: Agregar y eliminar contadores de los gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

    -   **Mostrar contador en la leyenda**: el error se agrega y selecciona en la leyenda. Para obtener más información, consulte [Usar la leyenda de la vista Diagramas para analizar pruebas de carga](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

    -   **Agregar gráfico**:

    1.  Se muestra el cuadro de diálogo **Escribir el nombre del gráfico**.

    2.  En el cuadro de texto **Nombre del gráfico**, escriba un nombre para el nuevo gráfico y elija **Aceptar**.

    3.  (Opcional) Vuelva a hacer clic con el botón derecho en el error y seleccione **Mostrar contador en el gráfico**.

         Para obtener más información, vea [Cómo: Crear gráficos personalizados](../test/how-to-create-custom-graphs-in-load-test-results.md).

5.  (Opcional) Si está analizando un error en un resultado de prueba de carga completada, considere la posibilidad de usar las características de zoom mientras está en la vista Gráficos. Para obtener más información, vea [Cómo: Acercar una región del gráfico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

    > [!TIP]
    > Si se detectara algún error durante la ejecución de la prueba de carga, en la barra de estado del Analizador de prueba de carga aparecería un vínculo titulado errores que incluiría el número encontrado. Puede elegir el vínculo para mostrar todos los errores en la tabla **Errores** de la vista Tablas.

## <a name="see-also"></a>Vea también

- [Usar el panel Contadores en la vista Gráficos y la vista Tablas](../test/counters-panel-in-load-test-analyzer.md)
- [Analizar resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)