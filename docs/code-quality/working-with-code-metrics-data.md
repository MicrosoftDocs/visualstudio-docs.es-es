---
title: "Resultados de métrica en Visual Studio de código | Documentos de Microsoft"
ms.custom: 
ms.date: 12/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 198e4b6d0ba2f3517cf907007cc544ca2e154013
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="working-with-code-metrics-data"></a>Trabajar con datos de métricas de código

El **resultados de métrica del código** ventana muestra los datos que se generan mediante el análisis de las métricas de código. Para obtener más información acerca de los valores de datos de métricas de código, vea [valores de métrica de código](../code-quality/code-metrics-values.md).

## <a name="displaying-code-metrics-results"></a>Mostrar resultados de métrica del código

El **resultados de métrica del código** ventana aparecerá automáticamente al generar resultados de métrica del código. También puede mostrar la ventana en cualquier momento.

### <a name="to-display-the-code-metrics-results-window"></a>Para mostrar la ventana Resultados de métrica del código

- En el **analizar** menú, elija **Windows** > **resultados de métrica del código**.

   \- o -

- En el **vista** menú, elija **otras ventanas** > **resultados de métrica del código**.

   El **resultados de métrica del código** se muestra la ventana, aunque no contenga ningún resultado.

### <a name="to-view-code-metrics-details"></a>Para ver los detalles de las métricas de código

Si se han generado los resultados de métrica del código, expanda el árbol en el **jerarquía** columna.

## <a name="filtering-code-metrics-results"></a>Filtrado de resultados de métrica del código

Puede filtrar los resultados que se muestran en la **resultados de métrica del código** ventana mediante el uso de la barra de herramientas en la parte superior. Por ejemplo, puede ver sólo los resultados que tienen un índice de mantenimiento inferior a 65.

El **filtro** cuadro de lista desplegable contiene los nombres de las columnas de resultados. Cuando se define un filtro, se agrega a la parte inferior de la lista junto con una sangría. La lista puede contener los últimos diez filtros que se definieron.

### <a name="to-filter-the-code-metrics-results"></a>Para filtrar los resultados de las métricas de código

1.  Desde el **filtro** , seleccione el nombre de columna.

2.  En **Min**, escriba el valor mínimo que se mostrará.

3.  En **Max**, escriba el valor máximo que se mostrará.

4.  Haga clic en el **aplicar filtro** botón.

5.  Para ver los detalles del resultado, expanda el árbol de jerarquía.

## <a name="adding-removing-and-rearranging-data-columns"></a>Agregar, quitar y reorganizar las columnas de datos

Puede agregar o quitar resultados de las columnas de la **resultados de métrica del código** ventana. Además, puede reorganizar las columnas de resultados para que aparezcan en el orden que desee.

### <a name="to-remove-a-column"></a>Para quitar una columna

1. Haga clic en el **agregar o quitar columnas** botón.

     \-o bien haga clic en cualquier encabezado de columna y, a continuación, haga clic en **agregar o quitar columnas**.

1. En el **agregar o quitar columnas** cuadro de diálogo, desactive la casilla de la columna que desea quitar y, a continuación, haga clic en **Aceptar**.

### <a name="to-add-a-previously-removed-column"></a>Para agregar una columna quitada previamente

1. Haga clic en el **agregar o quitar columnas** botón.

     \- o -

     Haga clic en cualquier encabezado de columna y, a continuación, haga clic en **agregar o quitar columnas**.

1. En el **agregar o quitar columnas** cuadro de diálogo, seleccione la casilla de verificación de la columna que desea agregar y, a continuación, haga clic en **Aceptar**.

### <a name="to-rearrange-columns"></a>Para reorganizar columnas

1. Haga clic en el **agregar o quitar columnas** botón.

     \- o -

     Haga clic en cualquier encabezado de columna y, a continuación, haga clic en **agregar o quitar columnas**.

1. En el **agregar o quitar columnas** cuadro de diálogo, seleccione la columna que desea mover y, a continuación, haga clic en la flecha arriba o flecha abajo.

1. Cuando se coloca la columna donde desee, haga clic en **Aceptar**.

## <a name="copying-data-to-the-clipboard-or-excel"></a>Copiar datos en el Portapapeles o Excel

Puede seleccionar y copiar una fila seleccionada de datos de métricas de código en el Portapapeles como una cadena de texto que contiene una línea por el nombre y valor de cada columna de datos. También puede hacer clic en **abrir la selección en Microsoft Excel** para exportar todos los resultados de las métricas de código a una hoja de cálculo de Excel.

## <a name="creating-a-work-item-based-on-code-metric-results"></a>Creación de un elemento de trabajo basado en los resultados de métrica de código

Puede crear un [Visual Studio Team Services (VSTS)](/vsts/index) elemento de trabajo que se basa en da como resultado la **resultados de métrica del código** ventana. Cuando se crea el elemento de trabajo, Visual Studio automáticamente entra en un título en el **título** datos de métricas de campo y el código en el **historial** ficha.

Para obtener más información acerca de VSTS, los elementos de trabajo, consulte [los elementos de trabajo](/vsts/work/work-items/index).

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

[Valores de métrica de código](../code-quality/code-metrics-values.md)  
[Cómo: Generar datos de las métricas de código](../code-quality/how-to-generate-code-metrics-data.md)