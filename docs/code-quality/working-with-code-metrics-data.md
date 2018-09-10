---
title: La ventana de resultados de las métricas de código en Visual Studio
ms.date: 12/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8400ce0d407af2318c4fffa19bc2b41e23f034d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44284143"
---
# <a name="using-the-code-metrics-results-window"></a>Uso de la ventana de resultados de las métricas de código

El **resultados de métrica del código** ventana muestra los datos que se generan mediante el análisis de las métricas de código. Para obtener más información acerca de los valores de datos de métricas de código, vea [valores de métricas de código](../code-quality/code-metrics-values.md).

## <a name="displaying-code-metrics-results"></a>Mostrar los resultados de las métricas de código

El **resultados de métrica del código** ventana aparece automáticamente cuando se generan los resultados de las métricas de código. También puede mostrar la ventana en cualquier momento.

### <a name="to-display-the-code-metrics-results-window"></a>Para mostrar la ventana de resultados de las métricas de código

- En el **analizar** menú, elija **Windows** > **resultados de métrica del código**.

   \- o -

- En el **vista** menú, elija **Other Windows** > **resultados de métrica del código**.

El **resultados de métrica del código** se muestra la ventana, incluso si no contiene ningún resultado.

### <a name="to-view-code-metrics-details"></a>Para ver los detalles de las métricas de código

Si se han generado los resultados de las métricas de código, expanda el árbol en el **jerarquía** columna.

## <a name="filtering-code-metrics-results"></a>Filtrar los resultados de las métricas de código

Puede filtrar los resultados que se muestran en el **resultados de métrica del código** ventana mediante el uso de la barra de herramientas en la parte superior. Por ejemplo, es posible que desee ver solo los resultados que tienen un índice de mantenimiento inferior a 65.

El **filtro** cuadro de lista desplegable contiene los nombres de las columnas de resultados. Cuando se define un filtro, se agrega a la parte inferior de la lista junto con una sangría. La lista puede contener los últimos diez filtros que se definieron.

### <a name="to-filter-the-code-metrics-results"></a>Para filtrar los resultados de las métricas de código

1.  Desde el **filtro** lista, seleccione el nombre de columna.

2.  En **Min**, escriba el valor mínimo que se mostrará.

3.  En **Max**, escriba el valor máximo que se mostrará.

4.  Haga clic en el **aplicar filtro** botón.

5.  Para ver los detalles de resultados, expanda el árbol de jerarquía.

## <a name="adding-removing-and-rearranging-data-columns"></a>Agregando, quitando y reorganizando columnas de datos

Puede agregar o quitar resultados de las columnas de la **resultados de métrica del código** ventana. Además, puede reorganizar las columnas de resultados para que aparezcan en el orden que desee.

### <a name="to-remove-a-column"></a>Para quitar una columna

1. Haga clic en el **agregar o quitar columnas** botón.

     \- o bien, haga clic en cualquier encabezado de columna y, a continuación, haga clic en **agregar o quitar columnas**.

1. En el **agregar o quitar columnas** cuadro de diálogo, desactive la casilla de la columna que desea quitar y, a continuación, haga clic en **Aceptar**.

### <a name="to-add-a-previously-removed-column"></a>Para agregar una columna que se han quitado previamente

1. Haga clic en el **agregar o quitar columnas** botón.

     \- o -

     Haga clic en cualquier encabezado de columna y, a continuación, haga clic en **agregar o quitar columnas**.

1. En el **agregar o quitar columnas** diálogo cuadro, active la casilla de verificación de la columna que desea agregar y, a continuación, haga clic en **Aceptar**.

### <a name="to-rearrange-columns"></a>Para reorganizar columnas

1. Haga clic en el **agregar o quitar columnas** botón.

     \- o -

     Haga clic en cualquier encabezado de columna y, a continuación, haga clic en **agregar o quitar columnas**.

1. En el **agregar o quitar columnas** cuadro de diálogo, seleccione la columna que desea mover y, a continuación, haga clic en la flecha arriba o flecha abajo.

1. Cuando se coloca la columna donde desee, haga clic en **Aceptar**.

## <a name="copying-data-to-the-clipboard-or-excel"></a>Copiar datos en el Portapapeles o Excel

Puede seleccionar y copiar una fila de datos de métricas de código seleccionada en el Portapapeles como una cadena de texto que contiene una línea para el nombre y valor de cada columna de datos. También puede hacer clic en **abrir la selección en Microsoft Excel** para exportar todos los resultados de las métricas de código a una hoja de cálculo de Excel.

## <a name="creating-a-work-item-based-on-code-metric-results"></a>Creación de un elemento de trabajo según los resultados de métrica de código

Puede crear un [paneles de Azure](/azure/devops/boards/index) da como resultado un elemento de trabajo que se basa en el **resultados de métrica del código** ventana. Cuando se crea el elemento de trabajo, Visual Studio entra automáticamente en un título en el **título** datos de métricas de campo y el código en el **historial** ficha.

Para obtener más información acerca de los paneles de Azure, los elementos de trabajo, consulte [los elementos de trabajo](/azure/devops/boards/work-items/index).

### <a name="to-create-a-work-item-based-on-a-result"></a>Para crear un elemento de trabajo basado en un resultado

1.  Haga clic en el resultado.

2.  Seleccione **crear elemento de trabajo**y, a continuación, haga clic en el tipo de elemento de trabajo que desea crear (**error**, **tarea**, y así sucesivamente).

3.  Complete el formulario de elemento de trabajo rellenando todos los campos obligatorios.

4.  En el **archivo** menú, haga clic en **guardar todo** para guardar el elemento de trabajo.

### <a name="to-create-a-bug-based-on-a-result"></a>Para crear un error basado en un resultado

1.  Haga clic en el resultado para seleccionarlo.

2.  Haga clic en el **crear elemento de trabajo** botón.

3.  Complete el formulario de elemento de trabajo rellenando todos los campos obligatorios.

4.  En el **archivo** menú, haga clic en **guardar todo** para guardar el elemento de trabajo.

## <a name="see-also"></a>Vea también

- [Valores de las métricas de código](../code-quality/code-metrics-values.md)
- [Cómo: generar datos de métricas de código](../code-quality/how-to-generate-code-metrics-data.md)