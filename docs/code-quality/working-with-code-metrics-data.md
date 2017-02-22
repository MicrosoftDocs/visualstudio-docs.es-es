---
title: "Trabajar con datos de m&#233;tricas de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codemetrics.output"
helpviewer_keywords: 
  - "resultados de métrica del código"
  - "Resultados de métrica del código (ventana)"
  - "ventana de resultados, métrica del código"
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 17
caps.handback.revision: 17
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# Trabajar con datos de m&#233;tricas de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La ventana **Resultados de métrica del código** muestra los datos generados por el análisis de las métricas del código.  Para obtener más información sobre los valores de datos de las métricas de código, vea [Valores de métrica de código](../code-quality/code-metrics-values.md).  
  
 Este tema contiene las siguientes secciones:  
  
-   [Resultados de métrica del código (ventana)](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)  
  
-   [Mostrar los resultados de métrica del código](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)  
  
-   [Filtrar los resultados de métrica del código](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)  
  
-   [Agregar, quitar y reorganizar columnas de datos](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)  
  
-   [Copiar datos en el portapapeles o Excel](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)  
  
-   [Crear un elemento de trabajo basado en resultados de métrica de código](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)  
  
##  <a name="BKMK_CodeMetricsResultsWindow"></a> Resultados de métrica del código \(ventana\)  
 La ventana **Resultados de métricas del código** tiene una barra de herramientas en la parte superior y columnas para mostrar los resultados calculados.  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Jerarquía**|La columna **Jerarquía** contiene una vista de árbol de la jerarquía del código que se puede expandir o contraer para ver el nivel de detalle necesario.  En las columnas restantes se muestran los resultados calculados.  Puede ocultar u organizar las columnas de resultados cuando desee.|  
|**Mantenibilidad**|La columna **Mantenimiento** contiene un icono además del resultado numérico.  Un icono verde indica un grado relativamente alto de facilidad de mantenimiento.  Un icono amarillo indica un grado moderado de facilidad de mantenimiento.  Un icono rojo indica una facilidad de mantenimiento baja y una fuente potencial de problemas.  Estos indicadores de color corresponden a las categorías de gravedad utilizadas por la regla AvoidUnmaintainableCode de FxCop.  Esta regla desencadena un error si el índice del mantenimiento es más bajo que 10, una advertencia si el índice está entre 10 y 20, y nada si el índice está por encima de 20.  El índice de mantenimiento es una síntesis de tres métricas: complejidad ciclomática, líneas de código y complejidad computacional.  Sus valores no se expresan en unidades.|  
  
##  <a name="BKMK_DisplayingCodeMetricsResults"></a> Mostrar los resultados de métrica del código  
 La ventana Resultados de métrica del código se muestra automáticamente al generar los resultados de las métricas del código.  También puede mostrar la ventana en cualquier momento.  
  
#### Para mostrar la ventana Resultados de métrica del código  
  
-   En el menú **Analizar** , haga clic en **Windows** y, a continuación, haga clic en **Resultados de métrica del código**.  
  
     – O bien –  
  
-   En el menú **Ver**, elija **Otras ventanas** y seleccione **Resultados de métrica del código**.  
  
     Aparecerá la ventana Resultados de métrica del código aunque no contenga ningún resultado.  
  
#### Para ver los detalles de métrica del código  
  
-   Si se han generado los resultados de las métricas del código, expanda el árbol en la columna **Jerarquía**.  
  
##  <a name="BKMK_FilteringCodeMetricsResults"></a> Filtrar los resultados de métrica del código  
 Puede filtrar los resultados que se muestran en la ventana **Resultados de métrica del código** mediante la barra de herramientas situada en la parte superior.  Por ejemplo, quizás desee ver solo los resultados con un índice de mantenimiento inferior a 65.  
  
 El cuadro desplegable **Filtro** contiene los nombres de las columnas de resultados.  Cuando se define un filtro, se agrega al final de la lista con una sangría.  La lista puede contener los últimos diez filtros que se definieron.  
  
#### Para filtrar los resultados de las métricas de código  
  
1.  En la lista **Filtro**, seleccione el nombre de la columna.  
  
2.  En **Mín.**, escriba el valor mínimo que se debe mostrar.  
  
3.  En **Máx.**, escriba el valor máximo que se debe mostrar.  
  
4.  Haga clic en el botón **Aplicar filtro**.  
  
5.  Para ver los detalles de los resultados, expanda el árbol de jerarquía.  
  
##  <a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> Agregar, quitar y reorganizar columnas de datos  
 Puede agregar o quitar columnas de resultados de la ventana **Resultados de métrica del código**.  Además, puede reorganizar las columnas de resultados de modo que aparezcan en el orden que desea.  
  
#### Para quitar una columna  
  
1.  Haga clic en el botón **Agregar o quitar columnas**.  
  
     – O bien –  
  
     Haga clic con el botón secundario del mouse en cualquier encabezado de columna y, a continuación, haga clic en **Agregar o quitar columnas**.  
  
2.  En el cuadro de diálogo **Agregar o quitar columnas**, desactive la casilla correspondiente a la columna que desee quitar y, a continuación, haga clic en **Aceptar**.  
  
#### Para agregar una columna quitada previamente  
  
1.  Haga clic en el botón **Agregar o quitar columnas**.  
  
     – O bien –  
  
     Haga clic con el botón secundario del mouse en cualquier encabezado de columna y, a continuación, haga clic en **Agregar o quitar columnas**.  
  
2.  En el cuadro de diálogo **Agregar o quitar columnas**, active la casilla correspondiente a la columna que desee agregar y, a continuación, haga clic en **Aceptar**.  
  
#### Para reorganizar las columnas  
  
1.  Haga clic en el botón **Agregar o quitar columnas**.  
  
     – O bien –  
  
     Haga clic con el botón secundario del mouse en cualquier encabezado de columna y, a continuación, haga clic en **Agregar o quitar columnas**.  
  
2.  En el cuadro de diálogo **Agregar o quitar columnas**, seleccione la columna que desee mover y, a continuación, haga clic en la flecha arriba o la flecha abajo.  
  
3.  Cuando la columna esté colocada en el lugar que desee, haga clic en **Aceptar**.  
  
##  <a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> Copiar datos en el portapapeles o Excel  
 Se puede seleccionar y copiar una fila seleccionada de datos codificados de métricas en el portapapeles como una cadena de texto que contiene una línea por nombre y valor de cada columna de datos.  También se puede hacer clic en **Abrir lista en Microsoft Excel** para exportar todos los resultados de métricas de código a una hoja de cálculo de Excel  
  
##  <a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> Crear un elemento de trabajo basado en resultados de métrica de código  
 Se puede crear un elemento de trabajo de [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] basado en resultados en la ventana de **Resultados de métrica de código** .  Cuando se crea el elemento de trabajo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se escribe automáticamente un título en el campo **Título** y datos de métricas de código bajo la pestaña **Historial** .  
  
 Para obtener más información sobre cómo crear elementos de trabajo, vea [Create a work item &#91;redirected&#93;](http://msdn.microsoft.com/es-es/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b).  
  
#### Para crear un elemento de trabajo basado en un resultado  
  
1.  Haga clic con el botón secundario del mouse en el resultado.  
  
2.  Elija **Crear elemento de trabajo** y, a continuación, haga clic en el tipo de elemento de trabajo que desee crear \(**Error**, **Tarea**, etc.\).  
  
3.  Complete el formulario de elemento de trabajo rellenando todos los campos obligatorios.  
  
4.  En el menú **Archivo**, haga clic en **Guardar todo** para guardar el elemento de trabajo.  
  
#### Para crear un error basado en un resultado  
  
1.  Haga clic en el resultado para seleccionarlo.  
  
2.  Haga clic en el botón **Crear elemento de trabajo**.  
  
3.  Complete el formulario de elemento de trabajo rellenando todos los campos obligatorios.  
  
4.  En el menú **Archivo**, haga clic en **Guardar todo** para guardar el elemento de trabajo.  
  
## Vea también  
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)   
 [Cómo: Generar datos de las métricas de código](../code-quality/how-to-generate-code-metrics-data.md)