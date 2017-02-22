---
title: "Filtrar las vistas de los informes de las Herramientas de generaci&#243;n de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de generación de perfiles, configurar"
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Filtrar las vistas de los informes de las Herramientas de generaci&#243;n de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede aplicar filtros a los archivos de datos de generación de perfiles para limitar los datos que se muestran en las vistas de los informes de rendimiento y que se exportan a los archivos de informe.  Puede limitar un informe a los datos entre valores de marcas de tiempo y puede limitar los datos a procesos y subprocesos concretos.  Puede guardar los filtros en un archivo y después crear un filtro en un archivo de datos de generación de perfiles diferente importando el filtro guardado.  
  
 También puede limitar un informe a un segmento horario utilizando la escala de tiempo gráfica de la vista de resumen.  Vea [Cómo: Filtrar vistas de informe desde la escala de tiempo de resumen](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md).  
  
 Para excluir código de sistema y de otros fabricantes de un informe, vea [Cómo: Filtrar vistas de informes para mostrar Solo mi código](../Topic/How%20to:%20Filter%20Profiling%20Tools%20Report%20Views%20to%20Display%20Just%20My%20Code.md)  
  
## Procedimientos  
  
#### Para crear un filtro de informe de generador de perfiles  
  
1.  Si no se muestra la ventana Filtrar vista de informe de rendimiento, haga clic en **Mostrar filtro** en la barra de herramientas de vista de informe de rendimiento.  
  
     El filtro de vistas de informe de rendimiento es una tabla.  Cada fila de la tabla representa una cláusula del filtro.  Puede agregar tantas cláusulas como desee a un filtro.  
  
2.  Para cada cláusula que desee agregar a un filtro, seleccione o especifique los valores en los siguientes campos de una fila.  
  
    |Campo|Descripción|  
    |-----------|-----------------|  
    |**y\/o**|Elija **Y** si tanto esta cláusula como la siguiente deben ser true para coincidir con un resultado.  Elija **O** si esta cláusula o la siguiente pueden ser true para coincidir con un resultado.|  
    |**Campo**|Seleccione el campo que se va a utilizar en la cláusula de filtro de la lista de campos de datos.|  
    |**operador ??**|Seleccione el operador que especifica la relación que desea en la cláusula entre el campo y el valor.<br /><br /> \=    Equals<br /><br /> \<\>  Not Equals<br /><br /> \<    Less Than<br /><br /> \>    Greater Than<br /><br /> \<\=  Less Than or Equals<br /><br /> \>\=  Greater Than or Equals|  
    |**Valor**|Seleccione o especifique el valor que desea buscar.  Algunos campos enumeran los valores disponibles para el campo.|  
  
#### Para crear un filtro de informe del generador de perfiles a partir de la vista de informe de marcas  
  
1.  En la barra de herramientas de la vista de datos, en la lista **Vista actual** seleccione **Marcas**.  
  
     Se muestra el informe de generador de perfiles de Marcas.  
  
2.  Seleccione el evento ETW o de muestreo que desea usar como punto inicial del informe.  
  
3.  Mantenga presionada la tecla CTRL y haga clic en el evento que desea usar como punto final del informe.  
  
4.  Haga clic con el botón secundario en una de las opciones siguientes:  
  
    -   **Agregar filtro a marcas** crea cláusulas de filtro que usan la columna Marca como campo de filtro.  
  
    -   **Agregar filtro a marcas de tiempo** crea las cláusulas de filtro que usan la columna Marca de tiempo en milisegundos como el campo de filtro.  
  
     Las dos opciones filtran el archivo de datos en los mismos puntos de inicio y final.  Ambas opciones sería buenas si exporta el filtro para usarlo en otros informes.  
  
#### Para cargar un filtro existente de un archivo  
  
1.  En la barra de herramientas de vista de informe de rendimiento, haga clic en **Importar filtro**.  
  
     Aparecerá el cuadro de diálogo **Cargar filtro**.  
  
2.  Especifique la ubicación y nombre de archivo para el archivo de filtro \(.vspf\) que se va a cargar.  
  
#### Para ejecutar un filtro  
  
-   En la barra de herramientas de vista de informe de rendimiento, haga clic en **Ejecutar filtro**.  
  
#### Para detener un filtro que tarda demasiado tiempo en ejecutarse  
  
-   En la barra de herramientas de vista de informe de rendimiento, haga clic en **Detener filtro**.  
  
#### Para quitar un filtro de una vista de informe  
  
1.  Elimine las filas de cláusulas del filtro de vista de informe de rendimiento.  
  
2.  En la barra de herramientas de vista de informe de rendimiento, haga clic en **Ejecutar filtro**.  
  
#### Para guardar un filtro en un archivo  
  
1.  En la barra de herramientas de vista de informe de rendimiento, haga clic en **Exportar filtro**.  
  
     Aparecerá el cuadro de diálogo **Guardar filtro**.  
  
2.  Especifique la ubicación y nombre de archivo para el archivo de filtro \(.vspf\) que se va a guardar.  
  
## Vea también  
 [Personalizar las vistas de los informes de las Herramientas de generación de perfiles](../profiling/customizing-performance-tools-report-views.md)