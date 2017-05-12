---
title: "Tutorial: Actualizar un gr&#225;fico en una hoja de c&#225;lculo utilizando botones de radio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "controles [desarrollo de Office en Visual Studio], actualizar hojas de cálculo"
  - "hojas de cálculo, actualizar utilizando controles administrados"
  - "hojas de cálculo, mediante botones de radio"
ms.assetid: cacc43a3-6d95-4a47-b943-3457d97a16f8
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# Tutorial: Actualizar un gr&#225;fico en una hoja de c&#225;lculo utilizando botones de radio
  En este tutorial se muestran los aspectos básicos del uso de los botones de radio en una hoja de cálculo de Microsoft Office Excel para proporcionar al usuario una forma de cambiar entre opciones rápidamente.  En este caso, las opciones cambian el estilo de un gráfico.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Para ver el resultado como un ejemplo completo, vea el ejemplo Excel Controls en [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar un grupo de botones de radio a una hoja de cálculo.  
  
-   Cambiar el estilo de gráfico cuando se selecciona una opción.  
  
> [!NOTE]  
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté usando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Agregar un gráfico a una hoja de cálculo  
 Puede crear un proyecto de libro de Excel que personalice un libro existente.  En este tutorial, agregará un gráfico a un libro y, a continuación, utilizará este libro en una nueva solución de Excel.  El origen de datos de este tutorial es una hoja de cálculo denominada **Datos para el gráfico**.  
  
#### Para agregar los datos  
  
1.  Abra Microsoft Excel.  
  
2.  Haga clic con el botón secundario en la ficha **Hoja3** y, a continuación, haga clic en **Cambiar nombre** en el menú contextual.  
  
3.  Cambie el nombre de la hoja a Datos para el gráfico.  
  
4.  Agregue los datos siguientes a **Datos para el gráfico** con la celda A4 como esquina superior izquierda y la celda E8 como esquina inferior derecha.  
  
    ||Q1|Q2|Q3|Q4|  
    |-|--------|--------|--------|--------|  
    |Oeste|500|550|550|600|  
    |Este|600|625|675|700|  
    |Norte|450|470|490|510|  
    |Sur|800|750|775|790|  
  
 A continuación, agregue un gráfico a la primera hoja de cálculo para mostrar los datos.  
  
#### Para agregar un gráfico en Excel  
  
1.  En el grupo **Gráficos** de la ficha **Insertar**, haga clic en **Columna** y después en **Todos los tipos de gráfico**.  
  
2.  En el cuadro de diálogo **Insertar gráfico**, haga clic en **Aceptar**.  
  
3.  En la ficha **Diseño**, en el grupo **Datos**, haga clic en **Seleccionar datos**.  
  
4.  En el cuadro de diálogo **Seleccionar origen de datos**, haga clic en el cuadro **Rangode datos del gráfico** y borre las selecciones predeterminadas.  
  
5.  En la hoja **Datos para el gráfico**, seleccione el bloque de celdas que contiene los números, desde A4 en la esquina superior izquierda hasta E8 en la esquina inferior derecha.  
  
6.  En el cuadro de diálogo **Seleccionar origen de datos**, haga clic en **Aceptar**.  
  
7.  Cambie de posición el gráfico para que la esquina superior derecha se alinee con la celda **E2**.  
  
8.  Guarde el archivo en la unidad C y denomínelo **ExcelChart.xlsx**.  
  
9. Salga de Excel.  
  
## Crear un proyecto nuevo  
 En este paso, creará un proyecto de libro de Excel basado en el libro **ExcelChart**.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre **Mi gráfico de Excel**.  En el asistente, seleccione **Copiar un documento existente**.  
  
     Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Haga clic en el botón y localicede **Examinar** el libro que creó anteriormente en este tutorial.  
  
3.  Haga clic en **Aceptar**.  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **Mi gráfico de Excel** al **Explorador de soluciones**.  
  
## Establecer las propiedades del gráfico  
 Cuando se crea un nuevo proyecto de libro de Excel que utiliza un libro existente, se crean automáticamente controles host para todos los rangos con nombre, los objetos de lista y los gráficos del libro.  Puede cambiar el nombre del control <xref:Microsoft.Office.Tools.Excel.Chart> utilizando la ventana **Propiedades**.  
  
#### Para cambiar el nombre del control Chart  
  
1.  Seleccione el control <xref:Microsoft.Office.Tools.Excel.Chart> en el diseñador y cambie las propiedades siguientes en la ventana **Propiedades**.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**dataChart**|  
    |**HasLegend**|**false**|  
  
## Agregar controles  
 Esta hoja de cálculo utiliza botones de radio para proporcionar a los usuarios una forma de cambiar rápidamente el estilo de gráfico.  Sin embargo, los botones de radio deben ser exclusivos: cuando se selecciona un botón no se puede seleccionar ningún otro botón del grupo al mismo tiempo.  Este comportamiento no se adquiere de forma predeterminada al agregar varios botones de radio a una hoja de cálculo.  
  
 Una forma de agregar este comportamiento consiste en agrupar los botones de radio en un control de usuario, escribir código subyacente en el control de usuario y, a continuación, agregar el control de usuario a la hoja de cálculo.  
  
#### Para agregar un control de usuario  
  
1.  Seleccione el proyecto **Mi gráfico de Excel** en el **Explorador de soluciones**.  
  
2.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Control de usuario**, asigne el nombre **ChartOptions** al control y haga clic en **Agregar**.  
  
#### Para agregar botones de radio al control de usuario  
  
1.  Si el control de usuario no está visible en el diseñador, haga doble clic en **ChartOptions** en el **Explorador de soluciones**.  
  
2.  Desde la ficha **Controles comunes** del **Cuadro de herramientas**, arrastre un control **RadioButton** hasta el control de usuario y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**columnChart**|  
    |**Texto**|Gráfico de columnas|  
  
3.  Agregue un segundo botón de radio al control de usuario y cambie las propiedades siguientes.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**barChart**|  
    |**Texto**|Gráfico de barras|  
  
4.  Agregue un tercer botón de radio al control de usuario y cambie las propiedades siguientes.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**lineChart**|  
    |**Texto**|Gráfico de líneas|  
  
5.  Agregue un cuarto botón de radio al control de usuario y cambie las propiedades siguientes.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**areaBlockChart**|  
    |**Texto**|Gráfico de bloques de áreas|  
  
 A continuación, escriba el código para actualizar el gráfico al hacer clic en un botón de radio.  
  
## Cambiar el estilo del gráfico cuando se selecciona un botón de radio  
 Ahora puede agregar el código para cambiar el estilo de gráfico.  Para ello, cree un evento público en el control de usuario, agregue una propiedad para establecer el tipo de selección y cree un controlador de eventos para el evento `CheckedChanged` de cada uno de los botones de radio.  
  
#### Para crear un evento y una propiedad en un control de usuario  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en el control de usuario y, a continuación, haga clic en **Ver código**.  
  
2.  Agregue código a la clase `ChartOptions` para crear un evento `SelectionChanged` y la propiedad `Selection`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#13)]  
  
#### Para controlar el evento CheckedChanged de los botones de radio  
  
1.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `areaBlockChart` y, a continuación, provoque el evento.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#14)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#14)]  
  
2.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `barChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#15)]  
  
3.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `columnChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#16)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#16](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#16)]  
  
4.  Establezca el tipo de gráfico en el controlador de eventos `CheckedChanged` del botón de radio `lineChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#17)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/ChartOptions.vb#17)]  
  
5.  En C\#, debe agregar controladores de eventos para los botones de radio.  Puede agregar el código al constructor `ChartOptions`, bajo la llamada a `InitializeComponent`.  Para obtener información acerca de cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/ChartOptions.cs#18)]  
  
## Agregar el control de usuario a la hoja de cálculo  
 Cuando se compila la solución, el nuevo control de usuario se agrega automáticamente al **Cuadro de herramientas**.  Puede arrastrar el control desde el **Cuadro de herramientas** a la hoja de cálculo.  
  
#### Para agregar el control de usuario a la hoja de cálculo  
  
1.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
     El control de usuario **ChartOptions** se agrega al **Cuadro de herramientas**.  
  
2.  En el **Explorador de soluciones**, haga clic con el botón secundario en **Sheet1.vb** o **Sheet1.cs** y, a continuación, haga clic en **Ver diseñador**.  
  
3.  Arrastre el control **ChartOptions** desde el **Cuadro de herramientas** hasta la hoja de cálculo.  
  
     Se agregará al proyecto un nuevo control denominado `my_Excel_Chart_ChartOptions1`.  
  
4.  Cambie el nombre del control por ChartOptions1.  
  
## Cambiar el tipo de gráfico  
 Para cambiar el tipo de gráfico, cree un controlador de eventos que establezca el estilo según la opción seleccionada en el control de usuario.  
  
#### Para cambiar el tipo de gráfico que se muestra en la hoja de cálculo  
  
1.  Agregue el siguiente controlador de eventos a la clase `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#19)]  
  
2.  En C\#, debe agregar un controlador de eventos para el control usuario al evento <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> como se muestra a continuación.  Para obtener información acerca de cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#20)]  
  
## Probar la aplicación  
 Ahora puede probar el libro para comprobar que el estilo aplicado al gráfico al seleccionar un botón de radio es correcto.  
  
#### Para probar el libro  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Seleccione distintos botones de radio.  
  
3.  Confirme que el estilo de gráfico cambia y coincide con la selección.  
  
## Pasos siguientes  
 En este tutorial se muestran los aspectos básicos del uso de los botones de radio y los estilos de gráfico en las hojas de cálculo.  Éstas son algunas de las tareas que pueden venir a continuación:  
  
-   Implementar el proyecto.  Para obtener más información, vea [Implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
-   Utilizar un botón para rellenar un cuadro de texto.  Para obtener más información, vea [Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
-   Cambiar el formato de una hoja de cálculo utilizando casillas.  Para obtener más información, vea [Tutorial: Cambiar el formato de una hoja de cálculo utilizando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## Vea también  
 [Tutoriales para Excel](../vsto/walkthroughs-using-excel.md)  
  
  