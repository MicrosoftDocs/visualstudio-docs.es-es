---
title: "Trabajar con datos de métricas de código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 39d45f5d43819dc418b6378d34a19e6af1d8ee12
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-code-metrics-data"></a>Trabajar con datos de métricas de código
El **resultados de métrica del código** ventana muestra los datos que se generan mediante el análisis de las métricas de código. Para obtener más información acerca de los valores de datos de métricas de código, vea [valores de métrica de código](../code-quality/code-metrics-values.md).  
  
 Este tema contiene las siguientes secciones:  
  
-   [Code Metrics Results Window](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [Mostrar resultados de métrica del código](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [Filtrado de resultados de métrica del código](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [Agregar, quitar y reorganizar las columnas de datos](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [Copiar datos en el Portapapeles o Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [Creación de un elemento de trabajo basado en los resultados de métrica de código](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window  
 El **resultados de métrica del código** ventana tiene una barra de herramientas en la parte superior y columnas que se muestran los resultados calculados.  
  
|Columna|Descripción|  
|------------|-----------------|  
|**Jerarquía de**|El **jerarquía** columna contiene una vista de árbol de la jerarquía de código que se puede expandir o contraer para ver el nivel de detalle que desee. Las columnas restantes muestran los resultados calculados. Puede ocultar u organizar las columnas de resultados como desee.|  
|**Facilidad de mantenimiento**|El **mantenimiento** columna contiene un icono además del resultado numérico. Un icono verde indica un grado relativamente alto de facilidad de mantenimiento. Un icono amarillo indica un grado moderado de facilidad de mantenimiento. Un icono rojo indica un potencial de problemas y de mantenimiento bajo. Estos indicadores de color se corresponden con las categorías de gravedad que se usan por la regla de FxCop AvoidUnmaintainableCode. Esta regla desencadena un error si el índice de mantenimiento es inferior a 10, una advertencia si el índice es entre 10 y 20 y un error ni una advertencia si el índice es mayor que 20. El índice de mantenimiento es una síntesis de tres métricas: complejidad ciclomática, líneas de código y la complejidad del cálculo. Sus valores no se expresan en unidades.|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a>Mostrar resultados de métrica del código  
 La ventana Resultados de métricas de código se muestra automáticamente cuando se generan resultados de métrica del código. También puede mostrar la ventana en cualquier momento.  
  
#### <a name="to-display-the-code-metrics-results-window"></a>Para mostrar la ventana Resultados de métrica del código  
  
-   En el **analizar** menú, haga clic en **Windows** y, a continuación, haga clic en **resultados de métrica del código**.  
  
     \- o -  
  
-   En el **vista** menú, elija **otras ventanas** y, a continuación, haga clic en **resultados de métrica del código**.  
  
     La ventana Resultados de métricas de código se muestra incluso cuando no contiene ningún resultado.  
  
#### <a name="to-view-code-metrics-details"></a>Para ver los detalles de las métricas de código  
  
-   Si se han generado los resultados de métrica del código, expanda el árbol en el **jerarquía** columna.  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a>Filtrado de resultados de métrica del código  
 Puede filtrar los resultados que se muestran en la **resultados de métrica del código** ventana mediante el uso de la barra de herramientas en la parte superior. Por ejemplo, puede ver sólo los resultados que tienen un índice de mantenimiento inferior a 65.  
  
 El **filtro** cuadro de lista desplegable contiene los nombres de las columnas de resultados. Cuando se define un filtro, se agrega a la parte inferior de la lista junto con una sangría. La lista puede contener los últimos diez filtros que se definieron.  
  
#### <a name="to-filter-the-code-metrics-results"></a>Para filtrar los resultados de las métricas de código  
  
1.  Desde el **filtro** , seleccione el nombre de columna.  
  
2.  En **Min**, escriba el valor mínimo que se mostrará.  
  
3.  En **Max**, escriba el valor máximo que se mostrará.  
  
4.  Haga clic en el **aplicar filtro** botón.  
  
5.  Para ver los detalles del resultado, expanda el árbol de jerarquía.  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a>Agregar, quitar y reorganizar las columnas de datos  
 Puede agregar o quitar resultados de las columnas de la **resultados de métrica del código** ventana. Además, puede reorganizar las columnas de resultados para que aparezcan en el orden que desee.  
  
#### <a name="to-remove-a-column"></a>Para quitar una columna  
  
1.  Haga clic en el **agregar o quitar columnas** botón.  
  
     \- o -  
  
     Haga clic en cualquier encabezado de columna y, a continuación, haga clic en **agregar o quitar columnas**.  
  
2.  En el **agregar o quitar columnas** cuadro de diálogo, desactive la casilla de la columna que desea quitar y, a continuación, haga clic en **Aceptar**.  
  
#### <a name="to-add-a-previously-removed-column"></a>Para agregar una columna quitada previamente  
  
1.  Haga clic en el **agregar o quitar columnas** botón.  
  
     \- o -  
  
     Haga clic en cualquier encabezado de columna y, a continuación, haga clic en **agregar o quitar columnas**.  
  
2.  En el **agregar o quitar columnas** cuadro de diálogo, seleccione la casilla de verificación de la columna que desea agregar y, a continuación, haga clic en **Aceptar**.  
  
#### <a name="to-rearrange-columns"></a>Para reorganizar columnas  
  
1.  Haga clic en el **agregar o quitar columnas** botón.  
  
     \- o -  
  
     Haga clic en cualquier encabezado de columna y, a continuación, haga clic en **agregar o quitar columnas**.  
  
2.  En el **agregar o quitar columnas** cuadro de diálogo, seleccione la columna que desea mover y, a continuación, haga clic en la flecha arriba o flecha abajo.  
  
3.  Cuando se coloca la columna donde desee, haga clic en **Aceptar**.  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a>Copiar datos en el Portapapeles o Excel  
 Puede seleccionar y copiar una fila seleccionada de datos de métricas de código en el Portapapeles como una cadena de texto que contiene una línea por el nombre y valor de cada columna de datos. También puede hacer clic en **lista abierta en Microsoft Excel** para exportar todos los resultados de las métricas de código a una hoja de cálculo de Excel  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a>Creación de un elemento de trabajo basado en los resultados de métrica de código  
 Puede crear un [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] elemento de trabajo que se basa en da como resultado la **resultados de métrica del código** ventana. Cuando se crea el elemento de trabajo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automáticamente entra en un título en el **título** datos de métricas de campo y el código en el **historial** ficha.  
  
 Para obtener más información sobre cómo crear elementos de trabajo, consulte [crear un elemento de trabajo &#91; redirigido &#93;](http://msdn.microsoft.com/en-us/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### <a name="to-create-a-work-item-based-on-a-result"></a>Para crear un elemento de trabajo basado en un resultado  
  
1.  Haga clic en el resultado.  
  
2.  Seleccione **crear elemento de trabajo**y, a continuación, haga clic en el tipo de elemento de trabajo que desea crear (**error**, **tarea**, y así sucesivamente).  
  
3.  Complete el formulario de elemento de trabajo rellenando todos los campos obligatorios.  
  
4.  En el **archivo** menú, haga clic en **guardar todo** para guardar el elemento de trabajo.  
  
#### <a name="to-create-a-bug-based-on-a-result"></a>Para crear un error basado en un resultado  
  
1.  Haga clic en el resultado para seleccionarlo.  
  
2.  Haga clic en el **crear elemento de trabajo** botón.  
  
3.  Complete el formulario de elemento de trabajo rellenando todos los campos obligatorios.  
  
4.  En el **archivo** menú, haga clic en **guardar todo** para guardar el elemento de trabajo.  
  
## <a name="see-also"></a>Vea también  
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Cómo: Generar datos de las métricas de código](../code-quality/how-to-generate-code-metrics-data.md)