---
title: Acercamiento de gráficos de resultados de pruebas de carga
description: Obtenga información sobre cómo examinar con más detalle los datos generados durante una ejecución de pruebas de carga usando barras de zoom para acercar una región del gráfico y desplazarse por ella.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: af780af58e3efa2aff7dc58971bfbbb881967c40
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879545"
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Cómo: Acercar una región del gráfico en los resultados de pruebas de carga

Una vez terminada una prueba de carga, puede usar las barras de zoom para acercar una región del gráfico y desplazarse por ella. Al aplicar el zoom para acercar, puede examinar los datos que se generaron durante la ejecución de una prueba de carga con más detalle.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

El zoom para acercar solo está disponible cuando analiza los resultados de una prueba de carga completada, no mientras observa los resultados de una prueba en ejecución.

El control de zoom solo es visible en el **Analizador de pruebas de carga** cuando se ven los resultados de una prueba de carga en modo de zoom. El modo de zoom se establece en la vista de gráficos cuando una prueba de carga se ha completado o cuando se carga una prueba de carga que se ha ejecutado previamente. Puede mostrar u ocultar los controles de zoom en los gráficos mediante **Mostrar controles de zoom** en la barra de herramientas.

Es posible ajustar el **zoom del eje x horizontal** para analizar determinados períodos de tiempo durante la prueba de carga. Se puede ajustar el **zoom del eje y vertical** para analizar determinados rangos de valores para los contadores que están incluidos en el gráfico.

Los controles de zoom de **escala de tiempo horizontal** y de **rango de valores vertical** se pueden ajustar mediante el mouse. El **control de escala de tiempo horizontal** también se puede ajustar mediante las teclas de dirección izquierda y derecha. Si se usan las teclas de dirección para ajustar el control de zoom, se puede ajustar el intervalo de ventanas en 1 intervalo de muestreo cada vez. Con las teclas **Mayús** y de dirección se realizan ajustes de diez intervalos de muestreo.

Para ajustar el control de zoom mediante las teclas de dirección, establezca primero el foco en el control de zoom con la tecla **Tab**. Cuando el control deslizante izquierdo tenga el foco, las teclas de dirección moverán el límite inicial de la ventana de zoom 1 intervalo a la izquierda o a la derecha. Cuando el foco esté en el control deslizante del centro, puede usar las teclas de dirección para desplazar la ventana de zoom a la izquierda o a la derecha 1 intervalo de muestreo sin cambiar el tamaño de la ventana de zoom. Y por último, el control deslizante derecho se desplaza, extendiendo o reduciendo el intervalo del final de la ventana de zoom 1 intervalo de muestreo.

Para que los controles de zoom horizontal y vertical vuelvan a mostrar la escala de tiempo y los intervalos de valores completos, puede usar la opción **Alejar horizontalmente**, **Alejar verticalmente** o **Alejar ambos** del menú emergente del gráfico.

> [!TIP]
> Puede usar **Sincronizar controles de zoom horizontal** de la barra de herramientas para activar o desactivar la sincronización de zoom horizontal automática. Con la sincronización activada, cualquier zoom que aplique a un gráfico también se aplica a cualquier otro gráfico de la vista de gráficos.

![Control de zoom de la vista de gráficos](../test/media/ltest_zoomcontrol.png)

En la ilustración anterior, se ha acercado el gráfico **Sistema a prueba** para investigar problemas de umbral. Las infracciones de umbral se han habilitado usando **Mostrar infracciones de umbral en el gráfico** en la lista desplegable **Opciones del gráfico** de la barra de herramientas.

Para obtener más información, vea [Analizar los resultados de pruebas de carga en la vista Gráficos](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="display-graphs"></a>Mostrar gráficos

Antes de cambiar la presentación de un gráfico acercándolo o alejándolo, o desplazándose por él, siga este procedimiento para mostrar gráficos.

Para mostrar los gráficos:

1. Ejecute una prueba de carga hasta que se complete.

2. Cuando termine la ejecución de la prueba de carga, elija **Sí** en el cuadro de diálogo en el que se le pregunta si quiere ver los resultados del almacén de resultados de pruebas de carga.

     \- o -

     Vea los detalles de una prueba de carga ejecutada anteriormente. Para más información, consulte [Acceso a los resultados de pruebas de carga para su análisis](../test/how-to-access-load-test-results-for-analysis.md).

3. Elija **Gráficos** si no se muestran los gráficos.

4. Si no se muestran las barras de zoom, elija **Mostrar controles de zoom**.

     Hay dos barras de zoom para cada gráfico. La barra de zoom que controla la escala vertical aparece a la izquierda del gráfico. La barra de zoom que controla la escala horizontal aparece debajo del gráfico.

     Cada barra de zoom tiene dos controladores. Un controlador es un área rectangular en cada extremo de la barra de zoom.

## <a name="zoom-and-scroll"></a>Zoom y desplazamiento

Cuando se muestran varios gráficos, puede mantenerlos sincronizados para que muestren la misma parte de la ejecución de la prueba de carga.

### <a name="to-synchronize-zooming-and-scrolling"></a>Para sincronizar el zoom y el desplazamiento

1. En el **Analizador de pruebas de carga**, elija **Sincronizar controles de zoom horizontal**.

     Cuando el botón **Sincronizar controles de zoom horizontal** está seleccionado, al aplicar zoom y desplazarse por la escala de tiempo de un determinado gráfico también se aplica zoom y se desplaza por la escala de tiempo de los demás gráficos.

2. De nuevo, elija **Sincronizar controles de zoom horizontal**.

     Cuando el botón **Sincronizar controles de zoom horizontal** no está seleccionado, el zoom y el desplazamiento por la escala de tiempo de un determinado gráfico solo afecta a ese gráfico.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Para aplicar zoom y desplazarse por una región del gráfico

1. En la barra de zoom bajo un gráfico, arrastre el controlador de la izquierda hacia la derecha.

     De esta forma, acercará la última parte de la ejecución de prueba. De igual forma, para acercar las primeras partes de la ejecución de prueba, arrastre el controlador derecho hacia la izquierda.

2. Para acercar una determinada área, deslice ambos controladores hacia el centro del gráfico.

     Cuanto más próximos entre sí estén los controladores, más se acerca con el zoom para mostrar segmentos más cortos y detallados de la prueba de carga.

     Elija la sección central de la barra de zoom y arrástrela para desplazarse a un punto determinado de la prueba de carga.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Para aplicar el zoom a una región del gráfico mediante la elección y el arrastre

1. Elija un gráfico en un extremo del área del zoom.

2. Arrastre el puntero del mouse hacia el otro extremo del área de zoom.

3. Suelte el botón del mouse (ratón).

    Esto ampliará el área que definió mediante la elección y el arrastre.

   En el procedimiento siguiente se describe cómo alejar un área rápidamente sin tener que ajustar los extremos de la barra de zoom.

### <a name="to-zoom-out"></a>Para alejar

1. Haga clic con el botón secundario del mouse en un gráfico al que se ha aplicado el zoom.

2. En el menú contextual, seleccione **Alejar horizontalmente**.

     Se aplicará el zoom para alejar y mostrar la duración completa de la ejecución de la prueba de carga.

## <a name="see-also"></a>Consulte también

- [Analizar los resultados de pruebas de carga en la vista Gráficos](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analizar los resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Cómo: Agregar y eliminar contadores de los gráficos de resultados de pruebas de carga](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)
