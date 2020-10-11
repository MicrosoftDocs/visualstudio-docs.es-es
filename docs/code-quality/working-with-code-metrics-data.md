---
title: Ventana de métricas de código
ms.date: 12/12/2017
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c01543b290d991a189c0851c64526c9c513068ba
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91927983"
---
# <a name="use-the-code-metrics-results-window"></a>Usar la ventana Resultados de métricas de código

La ventana **resultados de métricas de código** muestra los datos que genera el análisis de métricas de código. Para obtener más información sobre los valores de datos de métricas de código, vea [valores de métricas de código](../code-quality/code-metrics-values.md).

## <a name="display-code-metrics-results"></a>Mostrar resultados de métricas de código

La ventana **resultados de métricas de código** se muestra automáticamente cuando se generan resultados de métricas de código. También puede mostrar la ventana en cualquier momento.

Puede mostrar la ventana Resultados de métricas de código mediante una de las siguientes secuencias de menús:

- En el menú **analizar** , elija **Windows**  >  **resultados de métricas de código**de Windows.

- En el menú **Ver** , elija **otros**  >  **resultados de métricas de código**de Windows.

Se abre la ventana **resultados de métricas de código** , aunque no contenga ningún resultado.

### <a name="to-view-code-metrics-details"></a>Para ver los detalles de las métricas de código

Si se han generado resultados de métricas de código, expanda el árbol en la columna **jerarquía** .

## <a name="filter-code-metrics-results"></a>Filtrar resultados de métricas de código

Puede filtrar los resultados que se muestran en la ventana **resultados de métricas de código** mediante la barra de herramientas de la parte superior. Por ejemplo, puede que desee ver solo los resultados que tienen un índice de mantenimiento inferior a 65.

El cuadro desplegable **filtro** contiene los nombres de las columnas de resultados. Cuando se define un filtro, se agrega a la parte inferior de la lista junto con una sangría. La lista puede contener los últimos 10 filtros definidos.

### <a name="to-filter-the-code-metrics-results"></a>Para filtrar los resultados de las métricas de código

1. En la lista **filtro** , seleccione el nombre de la columna.

2. En **mín**, escriba el valor mínimo que se va a mostrar.

3. En **máx**, escriba el valor máximo que se va a mostrar.

4. Haga clic en el botón **aplicar filtro** .

5. Para ver los detalles del resultado, expanda el árbol de jerarquía.

## <a name="add-remove-and-rearrange-data-columns"></a>Agregar, quitar y reorganizar columnas de datos

Puede Agregar o quitar columnas de resultados en la ventana **resultados de métricas de código** . Además, puede reorganizar las columnas de resultados para que aparezcan en el orden que desee.

### <a name="add-or-remove-a-column"></a>Agregar o quitar una columna

1. Haga clic en el botón **Agregar o quitar columnas** o haga clic con el botón secundario en cualquier encabezado de columna y, a continuación, haga clic en **Agregar o quitar columnas**.

1. En el cuadro de diálogo **Agregar o quitar columnas** , Active o desactive la casilla de la columna que desea agregar o quitar y, a continuación, elija **Aceptar**.

### <a name="rearrange-columns"></a>Reorganizar columnas

1. Haga clic en el botón **Agregar o quitar columnas** .

1. En el cuadro de diálogo **Agregar o quitar columnas** , seleccione la columna que desea desplace y, a continuación, elija la flecha arriba o la flecha abajo.

1. Cuando la columna esté colocada donde desee, elija **Aceptar**.

## <a name="copy-data-to-the-clipboard-or-excel"></a>Copiar datos en el portapapeles o Excel

Puede seleccionar y copiar una fila seleccionada de datos de métricas de código en el portapapeles como una cadena de texto que contenga una línea para el nombre y el valor de cada columna de datos. También puede hacer clic en **abrir selección en Microsoft Excel** para exportar todos los resultados de las métricas de código a una hoja de cálculo de Excel.

## <a name="create-a-work-item-based-on-code-metric-results"></a>Crear un elemento de trabajo basado en resultados de métricas de código

Puede crear un elemento de trabajo de [Azure Boards](/azure/devops/boards/index?view=vsts&preserve-view=true) basado en resultados en la ventana **resultados de métricas de código** . Cuando se crea el elemento de trabajo, Visual Studio escribe automáticamente un título en el campo **título** y datos de métricas de código en la pestaña **historial** .

Para obtener más información sobre los elementos de trabajo de Azure Boards, vea [elementos de trabajo](/azure/devops/boards/work-items/index?view=vsts&preserve-view=true).

### <a name="to-create-a-work-item-based-on-a-result"></a>Para crear un elemento de trabajo basado en un resultado

1. Haga clic con el botón secundario en el resultado.

2. Elija **crear elemento de trabajo**y, a continuación, haga clic en el tipo de elemento de trabajo que desea crear (**error**, **tarea**, etc.).

3. Rellene todos los campos obligatorios para completar el formulario de elemento de trabajo.

4. En el menú **archivo** , haga clic en **guardar todo** para guardar el elemento de trabajo.

### <a name="to-create-a-bug-based-on-a-result"></a>Para crear un error basado en un resultado

1. Haga clic en el resultado para seleccionarlo.

2. Haga clic en el botón **crear elemento de trabajo** .

3. Rellene todos los campos obligatorios para completar el formulario de elemento de trabajo.

4. En el menú **archivo** , haga clic en **guardar todo** para guardar el elemento de trabajo.

## <a name="see-also"></a>Consulte también

- [Valores de las métricas de código](../code-quality/code-metrics-values.md)
- [Cómo: generar datos de métricas de código](../code-quality/how-to-generate-code-metrics-data.md)
