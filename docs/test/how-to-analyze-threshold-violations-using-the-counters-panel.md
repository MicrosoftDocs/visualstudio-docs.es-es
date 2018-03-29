---
title: Infracciones de umbral en pruebas de carga en Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, threshold violations
ms.assetid: 0126d7b7-0538-4ea9-9046-6556654b3b9d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 9c511bb3edf8ad8277b367733f85108d9587898e
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-analyze-threshold-violations-using-the-counters-panel-in-load-test-analyzer"></a>Cómo: Analizar las infracciones de reglas de umbral con el panel Contadores en el analizador de prueba de carga

El panel Contadores es visible en la vista Gráficos y en la vista Tablas del Analizador de prueba de carga mientras se está ejecutando una prueba de carga o cuando está analizando el resultado de una prueba de carga. Vea [Analizar los resultados de pruebas de carga en la vista Gráficos](../test/analyze-load-test-results-in-the-graphs-view.md), [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) y [Cómo: Obtener acceso a los resultados de pruebas de carga para su análisis](../test/how-to-access-load-test-results-for-analysis.md).

 Las infracciones de umbral están asociadas a contadores de rendimiento específicos e indican que un contador de rendimiento ha superado o no ha llegado a un valor de umbral especificado. Los iconos del panel Contadores indican las infracciones de umbral.

 ![Nodo Equipos del panel Contadores](../test/media/ltest_compnode.png "LTest_CompNode")

 El icono de una infracción de umbral se propaga desde el nodo donde reside el contador específico hasta la raíz. El icono alerta de una infracción en un contador que tal vez no esté visible en el árbol porque no se ha expandido. Un ejemplo del icono se puede ver en el nodo **Equipos** del panel Contadores en la ilustración anterior.

 El icono puede ser alguno de los siguientes:

 ![Ninguna infracción del umbral](../test/media/icon_ltest_1.gif "Icon_LTest_1") Ninguna infracción del umbral.

 ![Se ha producido una infracción del umbral grave en el último intervalo](../test/media/icon_ltest_2.gif "Icon_LTest_2") Se ha producido una infracción del umbral grave en el último intervalo.

 ![Se ha producido una infracción del umbral grave en un intervalo anterior](../test/media/icon_ltest_3.gif "Icon_LTest_3") Se ha producido una infracción del umbral grave en un intervalo anterior.

 ![Se ha producido una infracción del umbral de advertencia en el último intervalo](../test/media/icon_ltest_4.gif "Icon_LTest_4") Se ha producido una infracción del umbral de advertencia en el último intervalo.

 ![Se ha producido una infracción del umbral de advertencia en un intervalo anterior](../test/media/icon_ltest_5.gif "Icon_LTest_5") Se ha producido una infracción del umbral de advertencia en un intervalo anterior.

## <a name="to-analyze-threshold-violations-in-the-counters-panel"></a>Para analizar las infracciones de umbral en el panel Contadores

1.  Después de que se complete una prueba de carga, o después de cargar el resultado de una prueba, en la barra de herramientas del Analizador de pruebas de carga, elija **Gráficos** o **Tablas**.

     El panel Contadores se mostrará en la vista Gráficos o en la vista Tablas.

2.  Si el panel Contadores no está visible, elija **Mostrar panel de contadores** en la barra de herramientas.

     Cualquier nodo que contenga infracciones del umbral incluirá uno de los iconos enumerado anteriormente.

3.  Expanda el nodo que contiene un icono de umbral, como el nodo **Equipos**, como se muestra en la ilustración anterior "Nodo Equipos del panel Contadores con infracción del umbral". Continúe expandiendo el nodo hasta que llegue al contador de rendimiento con la infracción del umbral. Por ejemplo, la ilustración muestra la instancia con error de **Microsoft Virtual Machine Failed Bus Network Adapter**.

4.  (Opcional) Haga clic con el botón secundario en el contador de rendimiento con la infracción y seleccione una de las siguientes opciones:

    -   **Mostrar contador en el gráfico**: en la vista Gráficos, el contador de rendimiento se agrega y resalta en el gráfico seleccionado. Para obtener más información, vea [Cómo: Agregar y eliminar contadores de los gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

        > [!NOTE]
        > Los iconos de infracción de umbral también se pueden mostrar en el gráfico en la vista Gráficos. El icono de umbral aparece en el gráfico junto al punto de datos donde se ha producido la infracción de umbral. Para ello, elija la lista desplegable **Mostrar leyenda** en la barra de herramientas y seleccione **Mostrar infracciones de umbral en el gráfico**.

    -   **Mostrar contador en la leyenda**: el contador de rendimiento se agrega y selecciona en la leyenda. Para obtener más información, consulte [Usar la leyenda de la vista Diagramas para analizar pruebas de carga](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

    -   **Agregar gráfico**:

    1.  Se muestra el cuadro de diálogo **Escribir el nombre del gráfico**.

    2.  En el cuadro de texto **Nombre del gráfico**, escriba un nombre para el nuevo gráfico y elija **Aceptar**.

    3.  (Opcional) Vuelva a hacer clic con el botón derecho en el contador de rendimiento y seleccione **Mostrar contador en el gráfico**.

         Para obtener más información, vea [Cómo: Crear gráficos personalizados](../test/how-to-create-custom-graphs-in-load-test-results.md).

5.  (Opcional) Si está analizando la infracción del umbral en un resultado de prueba de carga completada, considere el uso de las características de zoom en la vista Gráficos. Para obtener más información, vea [Cómo: Acercar una región del gráfico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

    > [!TIP]
    > Si se detectara una infracción del umbral durante la ejecución de la prueba de carga, un vínculo denominado "infracciones del umbral", incluida la cantidad de infracciones, aparecerá en la barra de estado del Analizador de prueba de carga. Puede elegir el vínculo para mostrar todas las infracciones de umbral en la tabla **Umbrales** de la vista Tablas.

## <a name="see-also"></a>Vea también

- [Usar el panel Contadores en la vista Gráficos y la vista Tablas](../test/counters-panel-in-load-test-analyzer.md)
- [Analizar resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)