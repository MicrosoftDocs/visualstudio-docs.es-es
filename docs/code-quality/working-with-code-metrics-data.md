---
title: Ventana métricas de código
ms.date: 12/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: 6aa1de7b3c4a029038072e84bea1918ea33031db
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967173"
---
# <a name="use-the-code-metrics-results-window"></a>Utilice la ventana de resultados de las métricas de código

El **resultados de métrica del código** ventana muestra los datos que se generan mediante el análisis de las métricas de código. Para obtener más información acerca de los valores de datos de métricas de código, vea [valores de métricas de código](../code-quality/code-metrics-values.md).

## <a name="display-code-metrics-results"></a>Mostrar los resultados de las métricas de código

El **resultados de métrica del código** ventana aparece automáticamente cuando se generan los resultados de las métricas de código. También puede mostrar la ventana en cualquier momento.

Puede mostrar la ventana de resultados de las métricas de código mediante una de las siguientes secuencias de menú:

- En el **analizar** menú, elija **Windows** > **resultados de métrica del código**.

- En el **vista** menú, elija **Other Windows** > **resultados de métrica del código**.

El **resultados de métrica del código** abre la ventana, incluso si no contiene ningún resultado.

### <a name="to-view-code-metrics-details"></a>Para ver los detalles de las métricas de código

Si se han generado los resultados de las métricas de código, expanda el árbol en el **jerarquía** columna.

## <a name="filter-code-metrics-results"></a>Filtrar los resultados de las métricas de código

Puede filtrar los resultados que se muestran en el **resultados de métrica del código** ventana mediante el uso de la barra de herramientas en la parte superior. Por ejemplo, es posible que desee ver solo los resultados que tienen un índice de mantenimiento inferior a 65.

El **filtro** cuadro de lista desplegable contiene los nombres de las columnas de resultados. Cuando se define un filtro, se agrega a la parte inferior de la lista junto con una sangría. La lista puede contener los últimos 10 filtros que se definieron.

### <a name="to-filter-the-code-metrics-results"></a>Para filtrar los resultados de las métricas de código

1.  Desde el **filtro** lista, seleccione el nombre de columna.

2.  En **Min**, escriba el valor mínimo que se mostrará.

3.  En **Max**, escriba el valor máximo que se mostrará.

4.  Haga clic en el **aplicar filtro** botón.

5.  Para ver los detalles de resultados, expanda el árbol de jerarquía.

## <a name="add-remove-and-rearrange-data-columns"></a>Agregar, quitar y reorganizar las columnas de datos

Puede agregar o quitar resultados de las columnas de la **resultados de métrica del código** ventana. Además, puede reorganizar las columnas de resultados para que aparezcan en el orden que desee.

### <a name="add-or-remove-a-column"></a>Agregar o quitar una columna

1. Haga clic en el **agregar o quitar columnas** botón, o haga clic en cualquier encabezado de columna y, a continuación, haga clic en **agregar o quitar columnas**.

1. En el **agregar o quitar columnas** cuadro de diálogo, active o desactive la casilla de la columna que desea agregar o quitar y, a continuación, elija **Aceptar**.

### <a name="rearrange-columns"></a>Reorganizar columnas

1. Haga clic en el **agregar o quitar columnas** botón.

1. En el **agregar o quitar columnas** cuadro de diálogo, seleccione la columna que desea mover y, a continuación, elija la flecha arriba o flecha abajo.

1. Cuando se coloca la columna donde quiera, elija **Aceptar**.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Copiar datos en el Portapapeles o Excel

Puede seleccionar y copiar una fila de datos de métricas de código seleccionada en el Portapapeles como una cadena de texto que contiene una línea para el nombre y valor de cada columna de datos. También puede hacer clic en **abrir la selección en Microsoft Excel** para exportar todos los resultados de las métricas de código a una hoja de cálculo de Excel.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Crear un elemento de trabajo según los resultados de métrica de código

Puede crear un [paneles de Azure](/azure/devops/boards/index?view=vsts) da como resultado un elemento de trabajo que se basa en el **resultados de métrica del código** ventana. Cuando se crea el elemento de trabajo, Visual Studio entra automáticamente en un título en el **título** datos de métricas de campo y el código en el **historial** ficha.

Para obtener más información acerca de los paneles de Azure, los elementos de trabajo, consulte [los elementos de trabajo](/azure/devops/boards/work-items/index?view=vsts).

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