---
title: "Tutorial: Agregar controles a una hoja de c&#225;lculo en tiempo de ejecuci&#243;n en un proyecto de complemento de VSTO"
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
  - "complementos [desarrollo de Office en Visual Studio], agregar controles"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], agregar controles"
  - "controles [desarrollo de Office en Visual Studio], agregar a hojas de cálculo en tiempo de ejecución"
  - "hojas de cálculo, agregar controles en tiempo de ejecución"
ms.assetid: 4f68677a-4789-4564-b229-02e2d4031a5f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Tutorial: Agregar controles a una hoja de c&#225;lculo en tiempo de ejecuci&#243;n en un proyecto de complemento de VSTO
  Puede agregar controles a cualquier hoja de cálculo abierta mediante el uso de un complemento de VSTO de Excel.  Este tutorial muestra cómo usar la cinta para permitir a los usuarios agregar un <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> y <xref:Microsoft.Office.Tools.Excel.ListObject> a una hoja de cálculo.  Para obtener información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **Aplicación:** la información de este tema se aplica a los proyectos de complemento de VSTO para Excel.  Para obtener más información, consulte [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Proporcionar una interfaz de usuario \(UI\) para agregar controles a la hoja de cálculo.  
  
-   Agregar controles a la hoja de cálculo.  
  
-   Quitar controles de la hoja de cálculo.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## Crear un nuevo proyecto de complemento de VSTO de Excel  
 Comience creando un proyecto de complemento de VSTO de Excel.  
  
#### Para crear un nuevo proyecto de complemento de VSTO de Excel  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de complemento de VSTO de Excel con el nombre ExcelDynamicControls.  Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Agregue una referencia al ensamblado **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll**.  Esta referencia es obligatoria para agregar mediante programación un control de Windows Forms a una hoja de cálculo más adelante en este tutorial.  
  
## Proporcionar una interfaz de usuario para agregar controles a una hoja de cálculo  
 Agregue una pestaña personalizada a la cinta de Excel.  Los usuarios pueden seleccionar las casillas en la pestaña para agregar controles a una hoja de cálculo.  
  
#### Para proporcionar una interfaz de usuario para agregar controles a una hoja de cálculo  
  
1.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Cinta \(diseñador visual\)** y, a continuación, haga clic en **Agregar**.  
  
     Se abrirá un archivo denominado **Ribbon1.cs** o **Ribbon1.vb** en el diseñador de la cinta y mostrará una pestaña y un grupo predeterminados.  
  
3.  Desde la pestaña **Controles de la cinta de Office** del **Cuadro de herramientas**, arrastre un control CheckBox a **grupo1**.  
  
4.  Haga clic en **CheckBox1** para seleccionarlo.  
  
5.  En la ventana **Propiedades**, cambie las siguientes propiedades:  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Nombre**|Botón|  
    |**Etiqueta**|Botón|  
  
6.  Agregue una segunda casilla a **group1**, y, a continuación, cambie las siguientes propiedades.  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Nombre**|NamedRange|  
    |**Etiqueta**|NamedRange|  
  
7.  Agregue una tercera casilla a **group1**, y, a continuación, cambie las siguientes propiedades.  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Nombre**|ListObject|  
    |**Etiqueta**|ListObject|  
  
## Agregar controles a la hoja de cálculo  
 Los controles administrados solo pueden agregarse a elementos host, que actúan como contenedores.  Dado que los proyectos de complemento de VSTO funcionan con cualquier libro abierto, el complemento de VSTO convierte la hoja de cálculo en un elemento host u obtiene un elemento de host existente antes de agregar el control.  Agregue código a los controladores de eventos de clic de cada control para generar un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> que se basa en la hoja de cálculo abierta.  A continuación, agregue un <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> y <xref:Microsoft.Office.Tools.Excel.ListObject> en la selección actual en la hoja de cálculo.  
  
#### Para agregar controles a una hoja de cálculo  
  
1.  En el diseñador de la cinta, haga doble clic en **Button**.  
  
     El controlador de eventos <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> de la casilla **Button** se abre en el Editor de código.  
  
2.  Reemplace el controlador de eventos `Button_Click` por el siguiente código.  
  
     Este código usa el método `GetVstoObject` para obtener un elemento host que representa la primera hoja de cálculo del libro y, a continuación, agrega un control <xref:Microsoft.Office.Tools.Excel.Controls.Button> a la celda seleccionada actualmente.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#2)]  
  
3.  En el **Explorador de soluciones**, seleccione Ribbon1.cs o Ribbon1.vb.  
  
4.  En el menú **Ver**, haga clic en **Diseñador**.  
  
5.  En el diseñador de la cinta, haga doble clic en **NamedRange**.  
  
6.  Reemplace el controlador de eventos `NamedRange_Click` por el siguiente código.  
  
     Este código usa el método `GetVstoObject` para obtener un elemento host que representa la primera hoja de cálculo del libro y, a continuación, define un control <xref:Microsoft.Office.Tools.Excel.NamedRange> para la celda o celdas seleccionadas actualmente.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#3)]  
  
7.  En el diseñador de la cinta, haga doble clic en **ListObject**.  
  
8.  Reemplace el controlador de eventos `ListObject_Click` por el siguiente código.  
  
     Este código usa el método `GetVstoObject` para obtener un elemento host que representa la primera hoja de cálculo del libro y, a continuación, define un <xref:Microsoft.Office.Tools.Excel.ListObject> para la celda o celdas seleccionadas actualmente.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#4)]  
  
9. Agregue las siguientes instrucciones a la parte superior del archivo de código de la cinta.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#1)]  
  
## Quitar controles de la hoja de cálculo  
 Los controles no se conservan cuando se guarda y se cierra la hoja de cálculo.  Debería quitar mediante programación todos los controles de Windows Forms generados antes de que se guarde la hoja de cálculo o solo aparecerá un contorno del control cuando se vuelva a abrir el libro.  Agregue código al evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> que quita los controles de Windows Forms de la colección de controles del elemento host generado.  Para obtener más información, consulte [Guardar controles dinámicos en documentos de Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
#### Para quitar controles de la hoja de cálculo  
  
1.  En el **Explorador de soluciones**, seleccione ThisAddIn.cs o ThisAddIn.vb.  
  
2.  En el menú **Ver**, haga clic en **Código**.  
  
3.  Agregue el siguiente código a la clase ThisAddin.  Este código obtiene la primera hoja de cálculo del libro y, a continuación, usa el método `HasVstoObject` para comprobar si la hoja de cálculo tiene un objeto de hoja de cálculo generado.  Si el objeto de hoja de cálculo generado tiene controles, el código obtiene ese objeto de hoja de cálculo y recorre en iteración la colección de controles, quitando los controles.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#6)]  
  
4.  En C\# debe crear un controlador de eventos para el evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>.  Puede colocar este código en el método `ThisAddIn_Startup`.  Para obtener más información sobre cómo crear controladores de eventos, consulte [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  Reemplace el método `ThisAddIn_Startup` por el código siguiente.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#5)]  
  
## Probar la solución  
 Agregue controles a una hoja de cálculo seleccionándolos en una pestaña personalizada de la cinta.  Cuando guarde la hoja de cálculo, se quitarán estos controles.  
  
#### Para probar la solución.  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Seleccione cualquier celda de Hoja1.  
  
3.  Haga clic en la pestaña **Complementos**.  
  
4.  En el grupo **group1**, haga clic en **Button**.  
  
     Se mostrará un botón en la celda seleccionada.  
  
5.  Seleccione otra celda en Hoja1.  
  
6.  En el grupo **group1**, haga clic en **NamedRange**.  
  
     Se define un rango con nombre para la celda seleccionada.  
  
7.  Seleccione una serie de celdas en Hoja1.  
  
8.  En el grupo **group1**, haga clic en **ListObject**.  
  
     Se agrega un objeto de lista para las celdas seleccionadas.  
  
9. Guarde la hoja de cálculo.  
  
     Los controles que agregó a Hoja1 ya no aparecen.  
  
## Pasos siguientes  
 Puede obtener más información acerca de los controles en proyectos de complemento de Excel de VSTO en este tema:  
  
-   Para obtener información acerca de cómo guardar controles en una hoja de cálculo, vea la Muestra de controles dinámicos de complemento de VSTO de Excel en [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## Vea también  
 [Soluciones de Excel](../vsto/excel-solutions.md)   
 [Información general sobre controles de formularios Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [ListObject &#40;Control&#41;](../vsto/listobject-control.md)  
  
  