---
title: Trabajar con datos de métricas de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c2460b4e8b9e0b9043178989fcf8825815471be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645707"
---
# <a name="working-with-code-metrics-data"></a>Trabajar con datos de métricas de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La ventana **resultados de métricas de código** muestra los datos que genera el análisis de métricas de código. Para obtener más información sobre los valores de datos de métricas de código, vea [valores de métricas de código](../code-quality/code-metrics-values.md).

 Este tema contiene las siguientes secciones:

- [Ventana Resultados de métricas de código](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)

- [Mostrar resultados de métricas de código](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)

- [Filtrar resultados de métricas de código](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)

- [Agregar, quitar y reorganizar columnas de datos](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)

- [Copiar datos en el portapapeles o Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)

- [Crear un elemento de trabajo basado en resultados de métricas de código](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)

## <a name="code-metrics-results-window"></a><a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window
 La ventana **resultados de métricas de código** tiene una barra de herramientas en la parte superior y las columnas para mostrar los resultados calculados.

|Columna|Descripción|
|------------|-----------------|
|**Hierarchy**|La columna **Hierarchy** contiene una vista de árbol de la jerarquía de código que se puede expandir o contraer para ver el nivel de detalle que se desea. Las columnas restantes muestran los resultados calculados. Puede ocultar u organizar las columnas de resultados como desee.|
|**Capacidad de mantenimiento**|La columna de **mantenimiento** contiene un icono además del resultado numérico. Un icono verde indica un grado relativamente alto de mantenimiento. Un icono amarillo indica un grado moderado de mantenimiento. Un icono rojo indica un mantenimiento bajo y un posible problema. Estos indicadores de color se corresponden con las categorías de gravedad que usa la regla de FxCop AvoidUnmaintainableCode. Esta regla desencadena un error si el índice de mantenimiento es inferior a 10, una advertencia si el índice está entre 10 y 20, y ni un error ni una advertencia si el índice es superior a 20. El índice de mantenimiento es una síntesis de tres métricas: complejidad ciclomática, líneas de código y complejidad computacional. Sus valores no se expresan en unidades.|

## <a name="displaying-code-metrics-results"></a><a name="BKMK_DisplayingCodeMetricsResults"></a> Mostrar resultados de métricas de código
 La ventana Resultados de métricas de código se muestra automáticamente cuando se generan resultados de métricas de código. También puede mostrar la ventana en cualquier momento.

#### <a name="to-display-the-code-metrics-results-window"></a>Para mostrar la ventana Resultados de métricas de código

- En el menú **analizar** , haga clic en **ventanas** y, a continuación, haga clic en **resultados de métricas de código**.

     \- o -

- En el menú **Ver** , seleccione **otras ventanas** y, a continuación, haga clic en resultados de **métricas de código**.

     La ventana Resultados de métricas de código se muestra incluso cuando no contiene ningún resultado.

#### <a name="to-view-code-metrics-details"></a>Para ver los detalles de las métricas de código

- Si se han generado resultados de métricas de código, expanda el árbol en la columna **jerarquía** .

## <a name="filtering-code-metrics-results"></a><a name="BKMK_FilteringCodeMetricsResults"></a> Filtrar resultados de métricas de código
 Puede filtrar los resultados que se muestran en la ventana **resultados de métricas de código** mediante la barra de herramientas de la parte superior. Por ejemplo, puede que desee ver solo los resultados que tienen un índice de mantenimiento inferior a 65.

 El cuadro desplegable **filtro** contiene los nombres de las columnas de resultados. Cuando se define un filtro, se agrega a la parte inferior de la lista junto con una sangría. La lista puede contener los últimos diez filtros definidos.

#### <a name="to-filter-the-code-metrics-results"></a>Para filtrar los resultados de las métricas de código

1. En la lista **filtro** , seleccione el nombre de la columna.

2. En **mín**, escriba el valor mínimo que se va a mostrar.

3. En **máx**, escriba el valor máximo que se va a mostrar.

4. Haga clic en el botón **aplicar filtro** .

5. Para ver los detalles del resultado, expanda el árbol de jerarquía.

## <a name="adding-removing-and-rearranging-data-columns"></a><a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> Agregar, quitar y reorganizar columnas de datos
 Puede Agregar o quitar columnas de resultados en la ventana **resultados de métricas de código** . Además, puede reorganizar las columnas de resultados para que aparezcan en el orden que desee.

#### <a name="to-remove-a-column"></a>Para quitar una columna

1. Haga clic en el botón **Agregar o quitar columnas** .

     \- o -

     Haga clic con el botón secundario en cualquier encabezado de columna y haga clic en **Agregar o quitar columnas**.

2. En el cuadro de diálogo **Agregar o quitar columnas** , desactive la casilla de la columna que desea quitar y, a continuación, haga clic en **Aceptar**.

#### <a name="to-add-a-previously-removed-column"></a>Para agregar una columna quitada previamente

1. Haga clic en el botón **Agregar o quitar columnas** .

     \- o -

     Haga clic con el botón secundario en cualquier encabezado de columna y haga clic en **Agregar o quitar columnas**.

2. En el cuadro de diálogo **Agregar o quitar columnas** , active la casilla correspondiente a la columna que desea agregar y, a continuación, haga clic en **Aceptar**.

#### <a name="to-rearrange-columns"></a>Para reorganizar columnas

1. Haga clic en el botón **Agregar o quitar columnas** .

     \- o -

     Haga clic con el botón secundario en cualquier encabezado de columna y haga clic en **Agregar o quitar columnas**.

2. En el cuadro de diálogo **Agregar o quitar columnas** , seleccione la columna que desea desplace y, a continuación, haga clic en la flecha arriba o en la flecha abajo.

3. Cuando la columna esté colocada donde desee, haga clic en **Aceptar**.

## <a name="copying-data-to-the-clipboard-or-excel"></a><a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> Copiar datos en el portapapeles o Excel
 Puede seleccionar y copiar una fila seleccionada de datos de métricas de código en el portapapeles como una cadena de texto que contenga una línea para el nombre y el valor de cada columna de datos. También puede hacer clic en **Abrir lista en Microsoft Excel** para exportar todos los resultados de las métricas de código a una hoja de cálculo de Excel.

## <a name="creating-a-work-item-based-on-code-metric-results"></a><a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> Crear un elemento de trabajo basado en resultados de métricas de código
 Puede crear un [!INCLUDE[esprfound](../includes/esprfound-md.md)] elemento de trabajo basado en resultados en la ventana **resultados de métricas de código** . Cuando se crea el elemento de trabajo, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] escribe automáticamente un título en el campo **título** y datos de métricas de código en la pestaña **historial** .

 Para obtener más información sobre cómo crear elementos de trabajo, vea [crear un elemento de trabajo &#91;&#93;Redirigido ](https://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).

#### <a name="to-create-a-work-item-based-on-a-result"></a>Para crear un elemento de trabajo basado en un resultado

1. Haga clic con el botón secundario en el resultado.

2. Elija **crear elemento de trabajo**y, a continuación, haga clic en el tipo de elemento de trabajo que desea crear (**error**, **tarea**, etc.).

3. Rellene todos los campos obligatorios para completar el formulario de elemento de trabajo.

4. En el menú **archivo** , haga clic en **guardar todo** para guardar el elemento de trabajo.

#### <a name="to-create-a-bug-based-on-a-result"></a>Para crear un error basado en un resultado

1. Haga clic en el resultado para seleccionarlo.

2. Haga clic en el botón **crear elemento de trabajo** .

3. Rellene todos los campos obligatorios para completar el formulario de elemento de trabajo.

4. En el menú **archivo** , haga clic en **guardar todo** para guardar el elemento de trabajo.

## <a name="see-also"></a>Consulte también
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) [Cómo: generar datos de métricas de código](../code-quality/how-to-generate-code-metrics-data.md)
