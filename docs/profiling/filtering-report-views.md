---
title: Filtrar las vistas de informe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c5aaff542f654928a7ed56313232a6e6ead67f9d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="filtering-report-views"></a>Filtrar las vistas de informe
Puede aplicar filtros a los archivos de datos de generación de perfiles para limitar los datos que se muestran en las vistas de los informes de rendimiento y que se exportan a los archivos de informe. Puede limitar un informe a los datos entre valores de marcas de tiempo y puede limitar los datos a procesos y subprocesos concretos. Puede guardar los filtros en un archivo y después crear un filtro en un archivo de datos de generación de perfiles diferente importando el filtro guardado.  
  
 También puede limitar un informe a un segmento horario utilizando la escala de tiempo gráfica de la vista de resumen. Vea [Filtrado de vistas de informe desde la escala de tiempo de resumen](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
 Para excluir de un informe el código del sistema y de aplicaciones de terceros, vea [Cómo: filtrar vistas de herramientas de generación de perfiles para mostrar Solo mi código](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).  
  
## <a name="procedures"></a>Procedimientos  
  
#### <a name="to-create-a-profiler-report-filter"></a>Para crear un filtro de informe de generador de perfiles  
  
1.  Si no se muestra la ventana del filtro de vista Informe de rendimiento, haga clic en **Mostrar filtro** en la barra de herramientas de la vista Informe de rendimiento.  
  
     El filtro de vistas de informe de rendimiento es una tabla. Cada fila de la tabla representa una cláusula del filtro. Puede agregar tantas cláusulas como desee a un filtro.  
  
2.  Para cada cláusula que desee agregar a un filtro, seleccione o especifique los valores en los siguientes campos de una fila.  
  
    |Campo|Descripción|  
    |-----------|-----------------|  
    |**Y/O**|Elija **Y** si tanto esta cláusula como la siguiente deben ser true para coincidir con un resultado. Elija **O** si esta cláusula o la siguiente pueden ser true para coincidir con un resultado.|  
    |**Campo**|Seleccione el campo que se va a utilizar en la cláusula de filtro de la lista de campos de datos.|  
    |**Operator**|Seleccione el operador que especifica la relación que desea en la cláusula entre el campo y el valor.<br /><br /> =    Igual a<br /><br /> <>  No es igual a<br /><br /> <    Menor que<br /><br /> >    Mayor que<br /><br /> <=  Menor o igual que<br /><br /> >=  Mayor o igual que|  
    |**Valor**|Seleccione o especifique el valor que desea buscar. Algunos campos enumeran los valores disponibles para el campo.|  
  
3.  
  
#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Para crear un filtro de informe del generador de perfiles a partir de la vista de informe de marcas  
  
1.  Seleccione **Marcas** en la lista **Vista actual** de la barra de herramientas de la vista Informe de rendimiento.  
  
     Se muestra el informe de generador de perfiles de Marcas.  
  
2.  Seleccione el evento ETW o de muestreo que desea usar como punto inicial del informe.  
  
3.  Mantenga presionada la tecla CTRL y haga clic en el evento que desea usar como punto final del informe.  
  
4.  Haga clic con el botón secundario en una de las opciones siguientes:  
  
    -   **Agregar filtro a marcas** crea cláusulas de filtro que usan la columna Marca como campo de filtro.  
  
    -   **Agregar filtro a marcas de tiempo** crea las cláusulas de filtro que usan la columna Marca de tiempo en milisegundos como campo de filtro.  
  
     Las dos opciones filtran el archivo de datos en los mismos puntos de inicio y final. Ambas opciones sería buenas si exporta el filtro para usarlo en otros informes.  
  
#### <a name="to-load-an-existing-filter-from-a-file"></a>Para cargar un filtro existente de un archivo  
  
1.  En la barra de herramientas de la vista Informe de rendimiento, haga clic en **Importar filtro**.  
  
     Aparecerá el cuadro de diálogo **Cargar filtro**.  
  
2.  Especifique la ubicación y nombre de archivo para el archivo de filtro (.vspf) que se va a cargar.  
  
#### <a name="to-execute-a-filter"></a>Para ejecutar un filtro  
  
-   En la barra de herramientas de la vista Informe de rendimiento, haga clic en **Ejecutar filtro**.  
  
#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Para detener un filtro que tarda demasiado tiempo en ejecutarse  
  
-   En la barra de herramientas de la vista Informe de rendimiento, haga clic en **Detener filtro**.  
  
#### <a name="to-remove-a-filter-on-a-report-view"></a>Para quitar un filtro de una vista de informe  
  
1.  Elimine las filas de cláusulas del filtro de vista de informe de rendimiento.  
  
2.  En la barra de herramientas de la vista Informe de rendimiento, haga clic en **Ejecutar filtro**.  
  
#### <a name="to-save-a-filter-to-a-file"></a>Para guardar un filtro en un archivo  
  
1.  En la barra de herramientas de la vista Informe de rendimiento, haga clic en **Exportar filtro**.  
  
     Aparecerá el cuadro de diálogo **Guardar filtro**.  
  
2.  Especifique la ubicación y nombre de archivo para el archivo de filtro (.vspf) que se va a guardar.  
  
## <a name="see-also"></a>Vea también  
 [Personalizar las vistas de informes de las herramientas de rendimiento](../profiling/customizing-performance-tools-report-views.md)