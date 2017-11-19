---
title: "Tutorial: Actualizar un gráfico en una hoja de cálculo utilizando botones de Radio | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
ms.assetid: cacc43a3-6d95-4a47-b943-3457d97a16f8
caps.latest.revision: "58"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74bd005514fa2fe72450a95d84f38dd17a7b639f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Tutorial: Actualizar un gráfico en una hoja de cálculo utilizando botones de radio
  En este tutorial se muestra los aspectos básicos del uso de botones de radio en una hoja de cálculo de Microsoft Office Excel para proporcionar al usuario una manera de cambiar rápidamente entre las opciones. En este caso, las opciones cambian el estilo de un gráfico.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Para ver el resultado como un ejemplo completo, vea el ejemplo de controles de Excel en [ejemplos de desarrollo de Office y tutoriales](../vsto/office-development-samples-and-walkthroughs.md).  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar un grupo de botones de radio a una hoja de cálculo.  
  
-   Cambiar el estilo del gráfico cuando se selecciona una opción.  
  
> [!NOTE]  
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="adding-a-chart-to-a-worksheet"></a>Agregar un gráfico a una hoja de cálculo  
 Puede crear un proyecto de libro de Excel que se personaliza un libro existente. En este tutorial, agregará un gráfico a un libro y, a continuación, utilizará ese libro en una nueva solución de Excel. El origen de datos en este tutorial es una hoja de cálculo denominada **datos de gráfico**.  
  
#### <a name="to-add-the-data"></a>Para agregar los datos  
  
1.  Abra Microsoft Excel.  
  
2.  Haga clic en el **Sheet3** ficha y, a continuación, haga clic en **cambiar el nombre de** en el menú contextual.  
  
3.  Cambiar el nombre de la hoja a **datos de gráfico**.  
  
4.  Agregue los siguientes datos a **datos de gráfico** a la celda A4 la esquina superior izquierda esquina y la celda E8 la esquina inferior derecha.  
  
    ||Q1|Q2|Q3|T4|  
    |-|--------|--------|--------|--------|  
    |Oeste de|500|550|550|600|  
    |Este de|600|625|675|700|  
    |Norte|450|470|490|510|  
    |Sur|800|750|775|790|  
  
 A continuación, agregue un gráfico a la primera hoja de cálculo para mostrar los datos.  
  
#### <a name="to-add-a-chart-in-excel"></a>Para agregar un gráfico en Excel  
  
1.  En el **insertar** ficha la **gráficos** grupo, haga clic en **columna**y, a continuación, haga clic en **todos los tipos de gráfico**.  
  
2.  En el **Insertar gráfico** cuadro de diálogo, haga clic en **Aceptar**.  
  
3.  En el **diseño** ficha la **datos** grupo, haga clic en **seleccionar datos**.  
  
4.  En el **Seleccionar origen de datos** cuadro de diálogo, haga clic en el **Chartdata intervalo** cuadro y borre las selecciones predeterminadas.  
  
5.  En el **datos de gráfico** hoja, seleccione el bloque de celdas que contiene los números, que incluye A4 en la esquina superior izquierda hasta E8 en la esquina inferior derecha.  
  
6.  En el **Seleccionar origen de datos** cuadro de diálogo, haga clic en **Aceptar**.  
  
7.  Cambiar de posición el gráfico para que la esquina superior derecha se alinee con la celda **E2**.  
  
8.  Guarde el archivo a la unidad C y asígnele el nombre **ExcelChart.xlsx**.  
  
9. Salga de Excel.  
  
## <a name="creating-a-new-project"></a>Crear un proyecto nuevo  
 En este paso, creará un proyecto de libro de Excel basado en el **ExcelChart** libro.  
  
#### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre **Mi gráfico de Excel**. En el asistente, seleccione **copiar un documento existente**.  
  
     Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Haga clic en el **examinar** buttonand, busque el libro que creó anteriormente en este tutorial.  
  
3.  Haga clic en **Aceptar**.  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **Mi gráfico de Excel** proyecto al **el Explorador de soluciones**.  
  
## <a name="setting-properties-of-the-chart"></a>Establecer las propiedades del gráfico  
 Cuando se crea un nuevo proyecto de libro de Excel que usa un libro existente, automáticamente se crean para gráficos en el libro, objetos de lista y rangos con nombre de todos los controles host. Puede cambiar el nombre de la <xref:Microsoft.Office.Tools.Excel.Chart> control mediante el uso de la **propiedades** ventana.  
  
#### <a name="to-change-the-name-of-the-chart-control"></a>Para cambiar el nombre del control Chart  
  
1.  Seleccione el <xref:Microsoft.Office.Tools.Excel.Chart> controlar en el diseñador y cambie las siguientes propiedades en el **propiedades** ventana.  
  
    |Propiedad|Valor|  
    |--------------|-----------|  
    |**Nombre**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## <a name="adding-controls"></a>Agregar controles  
 Esta hoja de cálculo utiliza botones de radio para proporcionar a los usuarios un mecanismo para cambiar rápidamente el estilo del gráfico. Sin embargo, los botones de radio deben ser exclusivos: cuando se selecciona un botón, no se puede seleccionar ningún otro botón en el grupo al mismo tiempo. Este comportamiento no se produce de forma predeterminada al agregar varios botones de radio a una hoja de cálculo.  
  
 Una manera de agregar este comportamiento es agrupar los botones de opción en un control de usuario, escriba su código detrás del control de usuario y, a continuación, agregar el control de usuario a la hoja de cálculo.  
  
#### <a name="to-add-a-user-control"></a>Para agregar un control de usuario  
  
1.  Seleccione el **Mi gráfico de Excel** proyecto **el Explorador de soluciones**.  
  
2.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
3.  En el **Agregar nuevo elemento** cuadro de diálogo, haga clic en **Control de usuario**, nombre del control **ChartOptions** y haga clic en **agregar**.  
  
#### <a name="to-add-radio-buttons-to-the-user-control"></a>Para agregar botones de radio al control de usuario  
  
1.  Si el control de usuario no está visible en el diseñador, haga doble clic en **ChartOptions** en **el Explorador de soluciones**.  
  
2.  Desde el **controles comunes** pestaña de la **cuadro de herramientas**, arrastre un **botón de Radio** controlar al control de usuario y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |--------------|-----------|  
    |**Nombre**|**columnChart**|  
    |**Texto**|**Gráfico de columnas**|  
  
3.  Agregue un segundo botón de radio al control de usuario y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |--------------|-----------|  
    |**Nombre**|**barChart**|  
    |**Texto**|**Gráfico de barras**|  
  
4.  Agregue un tercer botón de radio al control de usuario y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |--------------|-----------|  
    |**Nombre**|**lineChart**|  
    |**Texto**|**Gráfico de líneas**|  
  
5.  Agregue un cuarto botón de radio al control de usuario y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |--------------|-----------|  
    |**Nombre**|**areaBlockChart**|  
    |**Texto**|**Gráfico de bloques de áreas**|  
  
 A continuación, escriba el código para actualizar el gráfico cuando se hace clic en un botón de radio.  
  
## <a name="changing-the-chart-style-when-a-radio-button-is-selected"></a>Cambiar el gráfico de estilo cuando un botón de Radio está seleccionado  
 Ahora puede agregar el código para cambiar el estilo del gráfico. Para ello, cree un evento público en el control de usuario, agregue una propiedad para establecer el tipo de selección y crear un controlador de eventos para el `CheckedChanged` eventos de cada uno de los botones de radio.  
  
#### <a name="to-create-an-event-and-property-on-a-user-control"></a>Para crear un evento y una propiedad en un control de usuario  
  
1.  En **el Explorador de soluciones**, haga clic en el control de usuario y, a continuación, haga clic en **ver código**.  
  
2.  Agregue código a la `ChartOptions` clase para crear un `SelectionChanged` eventos y `Selection` propiedad.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]  
  
#### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Para controlar el evento CheckedChanged de los botones de radio  
  
1.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `areaBlockChart` y, a continuación, genere el evento.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]  
  
2.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `barChart`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]  
  
3.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `columnChart`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]  
  
4.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `lineChart`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]  
  
5.  En C#, debe agregar controladores de eventos para los botones de radio. Puede agregar el código al constructor `ChartOptions`, debajo de la llamada a `InitializeComponent`. Para obtener información sobre cómo crear controladores de eventos, vea [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]  
  
## <a name="adding-the-user-control-to-the-worksheet"></a>Agregar el Control de usuario a la hoja de cálculo  
 Cuando se compila la solución, el nuevo control de usuario se agrega automáticamente a la **cuadro de herramientas**. A continuación, puede arrastrar el control desde el **cuadro de herramientas** a la hoja de cálculo.  
  
#### <a name="to-add-the-user-control-your-worksheet"></a>Para agregar el control de usuario de la hoja de cálculo  
  
1.  En el menú **Compilar** , haga clic en **Compilar solución**.  
  
     El **ChartOptions** control de usuario se agrega a la **cuadro de herramientas**.  
  
2.  En **el Explorador de soluciones**, haga clic en **Sheet1.vb** o **Sheet1.cs**y, a continuación, haga clic en **Diseñador de vistas**.  
  
3.  Arrastre el **ChartOptions** controlar desde la **cuadro de herramientas** a la hoja de cálculo.  
  
     Un nuevo control denominado `my_Excel_Chart_ChartOptions1` se agrega al proyecto.  
  
4.  Cambiar el nombre del control a **ChartOptions1**.  
  
## <a name="changing-the-chart-type"></a>Cambiar el tipo de gráfico  
 Para cambiar el tipo de gráfico, cree un controlador de eventos que establece el estilo de acuerdo con la opción seleccionada en el control de usuario.  
  
#### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Para cambiar el tipo de gráfico que se muestra en la hoja de cálculo  
  
1.  Agregue el siguiente controlador de eventos a la clase `Sheet1`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]  
  
2.  En C#, debe agregar un controlador de eventos para el control de usuario para el <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> eventos tal y como se muestra a continuación. Para obtener información sobre cómo crear controladores de eventos, vea [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]  
  
## <a name="testing-the-application"></a>Probar la aplicación  
 Ahora puede probar el libro para comprobar que el gráfico de estilo correctamente cuando se selecciona un botón de radio.  
  
#### <a name="to-test-your-workbook"></a>Para probar el libro  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Seleccione varios botones de radio.  
  
3.  Confirme que el estilo del gráfico cambia para coincidir con la selección.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En este tutorial se muestra los aspectos básicos del uso de botones de radio y los estilos de gráfico en las hojas de cálculo. A continuación, podría realizar las siguientes tareas:  
  
-   Implementar el proyecto. Para obtener más información, consulte [implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
-   Usar un botón para rellenar un cuadro de texto. Para obtener más información, consulte [Tutorial: mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
-   Cambiar el formato de una hoja de cálculo mediante el uso de casillas de verificación. Para obtener más información, consulte [Tutorial: cambiar hoja de cálculo formato utilizando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales para Excel](../vsto/walkthroughs-using-excel.md)  
  
  