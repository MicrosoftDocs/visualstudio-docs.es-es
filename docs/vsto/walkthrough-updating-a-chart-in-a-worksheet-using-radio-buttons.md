---
title: Actualizar gráfico en una hoja de cálculo mediante botones de radio
description: Conozca los aspectos básicos del uso de botones de radio en una hoja de cálculo de Microsoft Excel para proporcionar al usuario una manera de cambiar rápidamente entre las opciones.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, updating using managed controls
- controls [Office development in Visual Studio], updating worksheets
- worksheets, using radio buttons
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4e375f394cd3d8be35ace8e3df07920fb824a07e
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526059"
---
# <a name="walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons"></a>Tutorial: Actualizar un gráfico en una hoja de cálculo utilizando botones de radio
  En este tutorial se muestran los aspectos básicos del uso de botones de radio en una hoja de cálculo de Excel Microsoft Office para ofrecer al usuario una manera de cambiar rápidamente entre las opciones. En este caso, las opciones cambian el estilo de un gráfico.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Para ver el resultado como un ejemplo completado, vea el ejemplo de controles de Excel en [ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).

 En este tutorial se muestran las tareas siguientes:

- Agregar un grupo de botones de radio a una hoja de cálculo.

- Cambiar el estilo del gráfico cuando se selecciona una opción.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="add-a-chart-to-a-worksheet"></a>Agregar un gráfico a una hoja de cálculo
 Puede crear un proyecto de libro de Excel que personalice un libro existente. En este tutorial, agregará un gráfico a un libro y, a continuación, usará este libro en una nueva solución de Excel. El origen de datos de este tutorial es una hoja **de cálculo denominada Data for Chart**.

### <a name="to-add-the-data"></a>Para agregar los datos

1. Abra Microsoft Excel.

2. Haga clic con el botón secundario en la ficha **Sheet3** y, a continuación, haga clic en **cambiar nombre** en el menú contextual.

3. Cambiar el nombre de la hoja a **datos para el gráfico**.

4. Agregue los datos siguientes a los **datos del gráfico** con la celda A4 en la esquina superior izquierda y la celda E8 en la esquina inferior derecha.

   |Región/trimestre|T1|T2|T3|T4|
   |-|--------|--------|--------|--------|
   |West|500|550|550|600|
   |East|600|625|675|700|
   |North|450|470|490|510|
   |South|800|750|775|790|

   A continuación, agregue un gráfico a la primera hoja de cálculo para mostrar los datos.

### <a name="to-add-a-chart-in-excel"></a>Para agregar un gráfico en Excel

1. En la pestaña **Insertar** , en el grupo **gráficos** , haga clic en **columna** y, a continuación, haga clic en **todos los tipos de gráficos**.

2. En el cuadro de diálogo **Insertar gráfico** , haga clic en **Aceptar**.

3. En la pestaña **diseño** , en el grupo **datos** , haga clic en **seleccionar datos**.

4. En el cuadro de diálogo **Seleccionar origen de datos** , haga clic en el cuadro **intervalo de ChartData** y borre cualquier selección predeterminada.

5. En el **cuadro datos de la hoja de gráfico** , seleccione el bloque de celdas que contiene los números, que incluye A4 en la esquina superior izquierda a E8 en la esquina inferior derecha.

6. En el cuadro de diálogo **Seleccionar origen de datos** , haga clic en **Aceptar**.

7. Cambie la posición del gráfico para que la esquina superior derecha se alinee con la celda **E2**.

8. Guarde el archivo en la unidad C y asígnele el nombre **ExcelChart.xlsx**.

9. Salga de Excel.

## <a name="create-a-new-project"></a>Creación de un proyecto
 En este paso, creará un proyecto de libro de Excel basado en el libro **ExcelChart** .

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **mi gráfico de Excel**. En el asistente, seleccione **copiar un documento existente**.

     Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Haga clic en el botón **examinar** y busque el libro que creó anteriormente en este tutorial.

3. Haga clic en **OK**.

     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **Mis gráficos de Excel** a **Explorador de soluciones**.

## <a name="set-properties-of-the-chart"></a>Establecer las propiedades del gráfico
 Al crear un nuevo proyecto de libro de Excel que utiliza un libro existente, los controles host se crean automáticamente para todos los rangos con nombre, objetos de lista y gráficos del libro. Puede cambiar el nombre del <xref:Microsoft.Office.Tools.Excel.Chart> control mediante la ventana **propiedades** .

### <a name="to-change-the-name-of-the-chart-control"></a>Para cambiar el nombre del control Chart

1. Seleccione el <xref:Microsoft.Office.Tools.Excel.Chart> control en el diseñador y cambie las siguientes propiedades en la ventana **propiedades** .

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**Gráfico de gráficos**|
    |**HasLegend**|**false**|

## <a name="add-controls"></a>Agregar controles
 Esta hoja de cálculo usa botones de radio para proporcionar a los usuarios una forma de cambiar rápidamente el estilo del gráfico. Sin embargo, los botones de radio deben ser exclusivos: cuando se selecciona un botón, no se puede seleccionar ningún otro botón del grupo al mismo tiempo. Este comportamiento no se produce de forma predeterminada cuando se agregan varios botones de radio a una hoja de cálculo.

 Una manera de agregar este comportamiento es agrupar los botones de radio en un control de usuario, escribir el código subyacente del control de usuario y, a continuación, agregar el control de usuario a la hoja de cálculo.

### <a name="to-add-a-user-control"></a>Para agregar un control de usuario

1. Seleccione el proyecto **mi gráfico de Excel** en **Explorador de soluciones**.

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , haga clic en **control de usuario**, asigne al control el nombre **ChartOptions** y haga clic en **Agregar**.

### <a name="to-add-radio-buttons-to-the-user-control"></a>Para agregar botones de radio al control de usuario

1. Si el control de usuario no está visible en el diseñador, haga doble clic en **ChartOptions** en **Explorador de soluciones**.

2. En la pestaña **controles comunes** del **cuadro de herramientas**, arrastre un control botón de **radio** al control de usuario y cambie las siguientes propiedades.

   | Propiedad | Value |
   |----------|------------------|
   | **Nombre** | **columnChart** |
   | **Texto** | **Gráfico de columnas** |

3. Agregue un segundo botón de radio al control de usuario y cambie las siguientes propiedades.

   | Propiedad | Value |
   |----------|---------------|
   | **Nombre** | **barChart** |
   | **Texto** | **Gráfico de barras** |

4. Agregue un tercer botón de radio al control de usuario y cambie las siguientes propiedades.

   | Propiedad | Value |
   |----------|----------------|
   | **Nombre** | **lineChart** |
   | **Texto** | **Gráfico de líneas** |

5. Agregue un cuarto botón de radio al control de usuario y cambie las siguientes propiedades.

   |Propiedad|Value|
   |--------------|-----------|
   |**Nombre**|**areaBlockChart**|
   |**Texto**|**Gráfico de bloques de áreas**|

   A continuación, escriba el código para actualizar el gráfico cuando se haga clic en un botón de radio.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Cambiar el estilo del gráfico cuando se selecciona un botón de radio
 Ahora puede Agregar el código para cambiar el estilo del gráfico. Para ello, cree un evento público en el control de usuario, agregue una propiedad para establecer el tipo de selección y cree un controlador de eventos para el `CheckedChanged` evento de cada uno de los botones de radio.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Para crear un evento y una propiedad en un control de usuario

1. En **Explorador de soluciones**, haga clic con el botón secundario en el control de usuario y, a continuación, haga clic en **Ver código**.

2. Agregue código a la `ChartOptions` clase para crear un `SelectionChanged` evento y la `Selection` propiedad.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#13)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#13)]

### <a name="to-handle-the-checkedchanged-event-of-the-radio-buttons"></a>Para controlar el evento CheckedChanged de los botones de radio

1. Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `areaBlockChart` y, a continuación, genere el evento.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#14)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#14)]

2. Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `barChart`.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#15)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#15)]

3. Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `columnChart`.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#16)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#16)]

4. Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `lineChart`.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/VisualBasic/my excel chart/ChartOptions.vb#17)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#17)]

5. En C#, debe agregar controladores de eventos para los botones de radio. Puede agregar el código al constructor `ChartOptions`, debajo de la llamada a `InitializeComponent`. Para obtener información sobre cómo crear controladores de eventos, consulte [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/ChartOptions.cs#18)]

## <a name="add-the-user-control-to-the-worksheet"></a>Agregar el control de usuario a la hoja de cálculo
 Al compilar la solución, el nuevo control de usuario se agrega automáticamente al **cuadro de herramientas**. A continuación, puede arrastrar el control desde el **cuadro de herramientas** a la hoja de cálculo.

### <a name="to-add-the-user-control-your-worksheet"></a>Para agregar el control de usuario a la hoja de cálculo

1. En el menú **Compilar** , haga clic en **Compilar solución**.

     El control de usuario **ChartOptions** se agrega al **cuadro de herramientas**.

2. En **Explorador de soluciones**, haga clic con el botón secundario en **Hoja1. VB** o **Sheet1.CS** y, a continuación, haga clic en **Ver diseñador**.

3. Arrastre el control **ChartOptions** desde el **cuadro de herramientas** a la hoja de cálculo.

     Se agrega un nuevo control denominado `my_Excel_Chart_ChartOptions1` al proyecto.

4. Cambie el nombre del control a **ChartOptions1**.

## <a name="change-the-chart-type"></a>Cambiar el tipo de gráfico
 Para cambiar el tipo de gráfico, cree un controlador de eventos que establezca el estilo de acuerdo con la opción seleccionada en el control de usuario.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-worksheet"></a>Para cambiar el tipo de gráfico que se muestra en la hoja de cálculo

1. Agrega el siguiente controlador de eventos a la clase `Sheet1`.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#19)]
     [!code-cs[Trin_VstcoreProgrammingControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#19)]

2. En C#, debe agregar un controlador de eventos para el control de usuario al <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> evento, tal como se muestra a continuación. Para obtener información sobre cómo crear controladores de eventos, consulte [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-cs[Trin_VstcoreProgrammingControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#20)]

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el libro para comprobar que el estilo del gráfico es correcto cuando se selecciona un botón de radio.

### <a name="to-test-your-workbook"></a>Para probar el libro

1. Presione **F5** para ejecutar el proyecto.

2. Seleccione varios botones de radio.

3. Confirme que el estilo del gráfico cambia para coincidir con la selección.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los aspectos básicos del uso de botones de radio y estilos de gráfico en hojas de cálculo. A continuación, podría realizar las siguientes tareas:

- Implementar el proyecto. Para obtener más información, vea [implementar una solución de Office](../vsto/deploying-an-office-solution.md).

- Usar un botón para rellenar un cuadro de texto. Para obtener más información, vea [Tutorial: mostrar texto en un cuadro de texto de una hoja de cálculo mediante un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).

- Cambiar el formato de una hoja de cálculo mediante las casillas. Para obtener más información, vea [Tutorial: cambiar el formato de una hoja de cálculo mediante controles de casilla](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Consulte también
- [Tutoriales de uso de Excel](../vsto/walkthroughs-using-excel.md)
