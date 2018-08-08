---
title: Valores de trazado para contadores de gráficos en pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, graphing counters
ms.assetid: 1969c20b-e0eb-48f6-a49f-a9090cd86008
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 5df33a8cf05e4ad73b1643e2948392e49a32356e
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382326"
---
# <a name="how-to-specify-plot-options-for-graphing-counters"></a>Cómo: Especificar opciones de trazado para contadores de gráficos

El cuadro de diálogo **Opciones de trazado** permite cambiar el color y estilo de línea de un contador trazado en un gráfico. Puede corregir también el intervalo en un valor concreto o establecer el intervalo que se va a ajustar automáticamente, según los datos de ejemplo.

![Cuadro de diálogo Opciones de trazado](../test/media/ltest_plotoptions.png)

## <a name="to-specify-plotting-options-for-graphs"></a>Para especificar opciones de trazado de gráficos

1.  En el **Analizador de pruebas de carga**, elija **Gráficos** en la barra de herramientas.

     Se muestran los resultados de las pruebas de carga en una vista de gráfico.

2.  En la leyenda o en el gráfico, haga clic con el botón derecho en la fila o la línea de trazado actual del contador de rendimiento cuya opción de trazado quiere cambiar y luego seleccione **Opciones de trazado**.

     Aparecerá el cuadro de diálogo **Opciones de trazado**.

3.  Utilice la lista desplegable **Color** y seleccione el color que desea utilizar para trazar el contador de rendimiento.

4.  Utilice la lista desplegable **Estilo** y seleccione el estilo que desea utilizar para trazar el contador de rendimiento.

5.  Realice una de las siguientes acciones:

     Seleccione **Ajustar intervalo automáticamente** (valor predeterminado)

     \- o -

     Borre **Ajustar intervalo automáticamente** y utilice la lista desplegable **Intervalo** para especificar el intervalo que desea utilizar para trazar el contador de rendimiento.

6.  Elija **Aceptar**.

     El contador de rendimiento para el que cambió las opciones se muestra en el gráfico con los cambios que especificó.

## <a name="see-also"></a>Vea también

- [Analizar los resultados de pruebas de carga en la vista Gráficos](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Cómo: Crear gráficos personalizados](../test/how-to-create-custom-graphs-in-load-test-results.md)
