---
title: 'Tutorial: Agregar controles a una hoja de cálculo en tiempo de ejecución en un proyecto de complemento de VSTO'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a8dde4832a128dd061f8a0982158ac1074f94820
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875815"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-runtime-in-vsto-add-in-project"></a>Tutorial: Agregar controles a una hoja de cálculo en tiempo de ejecución en un proyecto de complemento de VSTO
  Puede agregar controles a cualquier hoja de cálculo abierta mediante el uso de un complemento de VSTO de Excel. Este tutorial muestra cómo usar la cinta para permitir a los usuarios agregar un <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> y <xref:Microsoft.Office.Tools.Excel.ListObject> a una hoja de cálculo. Para obtener información, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 **Se aplica a:** La información de este tema se aplica a los proyectos de complemento VSTO para Excel. Para obtener más información, consulte [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 En este tutorial se muestran las tareas siguientes:  
  
- Proporcionar una interfaz de usuario (UI) para agregar controles a la hoja de cálculo.  
  
- Agregar controles a la hoja de cálculo.  
  
- Quitar controles de la hoja de cálculo.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## <a name="create-a-new-excel-vsto-add-in-project"></a>Cree un nuevo proyecto de complemento VSTO de Excel  
 Comience creando un proyecto de complemento de VSTO de Excel.  
  
### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Para crear un nuevo proyecto de complemento de VSTO de Excel  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de complemento VSTO de Excel con el nombre **ExcelDynamicControls**. Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Agregue una referencia a la **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** ensamblado. Esta referencia es obligatoria para agregar mediante programación un control de Windows Forms a una hoja de cálculo más adelante en este tutorial.  
  
## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Proporcionar una interfaz de usuario para agregar controles a una hoja de cálculo  
 Agregue una pestaña personalizada a la cinta de Excel. Los usuarios pueden seleccionar las casillas en la pestaña para agregar controles a una hoja de cálculo.  
  
#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Para proporcionar una interfaz de usuario para agregar controles a una hoja de cálculo  
  
1.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
2.  En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **cinta (diseñador Visual)** y, a continuación, haga clic en **agregar**.  
  
     Un archivo denominado **Ribbon1.cs** o **Ribbon1.vb** se abre en el Diseñador de cinta de opciones y muestra una ficha predeterminada y un grupo.  
  
3.  Desde el **controles de la cinta de Office** pestaña de la **cuadro de herramientas**, arrastre un control CheckBox **group1**.  
  
4.  Haga clic en **CheckBox1** para seleccionarlo.  
  
5.  En la ventana **Propiedades** , cambie las siguientes propiedades:  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**Button**|  
    |**Label**|**Button**|  
  
6.  Agregue una segunda casilla a **group1**, y, a continuación, cambie las siguientes propiedades.  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**NamedRange**|  
    |**Label**|**NamedRange**|  
  
7.  Agregue una tercera casilla a **group1**y, a continuación, cambie las siguientes propiedades.  
  
    |Property|Valor|  
    |--------------|-----------|  
    |**Name**|**ListObject**|  
    |**Label**|**ListObject**|  
  
## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo  
 Los controles administrados solo pueden agregarse a elementos host, que actúan como contenedores. Dado que los proyectos de complemento de VSTO funcionan con cualquier libro abierto, el complemento de VSTO convierte la hoja de cálculo en un elemento host u obtiene un elemento de host existente antes de agregar el control. Agregue código a los controladores de eventos de clic de cada control para generar un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> que se basa en la hoja de cálculo abierta. A continuación, agregue un <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange> y <xref:Microsoft.Office.Tools.Excel.ListObject> en la selección actual en la hoja de cálculo.  
  
### <a name="to-add-controls-to-a-worksheet"></a>Para agregar controles a una hoja de cálculo  
  
1.  En el Diseñador de cinta de opciones, haga doble clic en **botón**.  
  
     El <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> controlador de eventos de la **botón** casilla de verificación se abre en el Editor de código.  
  
2.  Reemplace el controlador de eventos `Button_Click` por el siguiente código:  
  
     Este código usa el método `GetVstoObject` para obtener un elemento host que representa la primera hoja de cálculo del libro y, a continuación, agrega un control <xref:Microsoft.Office.Tools.Excel.Controls.Button> a la celda seleccionada actualmente.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]  
  
3.  En **el Explorador de soluciones**, seleccione *Ribbon1.cs* o *Ribbon1.vb*.  
  
4.  En el **vista** menú, haga clic en **diseñador**.  
  
5.  En el Diseñador de cinta de opciones, haga doble clic en **NamedRange**.  
  
6.  Reemplace el controlador de eventos `NamedRange_Click` por el siguiente código:  
  
     Este código usa el método `GetVstoObject` para obtener un elemento host que representa la primera hoja de cálculo del libro y, a continuación, define un control <xref:Microsoft.Office.Tools.Excel.NamedRange> para la celda o celdas seleccionadas actualmente.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]  
  
7.  En el Diseñador de cinta de opciones, haga doble clic en **ListObject**.  
  
8.  Reemplace el controlador de eventos `ListObject_Click` por el siguiente código:  
  
     Este código usa el método `GetVstoObject` para obtener un elemento host que representa la primera hoja de cálculo del libro y, a continuación, define un <xref:Microsoft.Office.Tools.Excel.ListObject> para la celda o celdas seleccionadas actualmente.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]  
  
9. Agregue las siguientes instrucciones a la parte superior del archivo de código de la cinta.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]  
  
## <a name="remove-controls-from-the-worksheet"></a>Quitar controles de la hoja de cálculo  
 Los controles no se conservan cuando se guarda y se cierra la hoja de cálculo. Debería quitar mediante programación todos los controles de Windows Forms generados antes de que se guarde la hoja de cálculo o solo aparecerá un contorno del control cuando se vuelva a abrir el libro. Agregue código al evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> que quita los controles de Windows Forms de la colección de controles del elemento host generado. Para obtener más información, consulte [Guardar controles dinámicos en documentos de Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
### <a name="to-remove-controls-from-the-worksheet"></a>Para quitar controles de la hoja de cálculo  
  
1.  En **el Explorador de soluciones**, seleccione *ThisAddIn.cs* o *ThisAddIn.vb*.  
  
2.  En el **vista** menú, haga clic en **código**.  
  
3.  Agregue el método siguiente a la clase `ThisAddIn`. Este código obtiene la primera hoja de cálculo del libro y, a continuación, usa el método `HasVstoObject` para comprobar si la hoja de cálculo tiene un objeto de hoja de cálculo generado. Si el objeto de hoja de cálculo generado tiene controles, el código obtiene ese objeto de hoja de cálculo y recorre en iteración la colección de controles, quitando los controles.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]  
  
4.  En C# debe crear un controlador de eventos para el evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave>. Puede colocar este código en el método `ThisAddIn_Startup`. Para obtener más información acerca de cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md). Reemplace el método `ThisAddIn_Startup` por el código siguiente.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]  
  
## <a name="test-the-solution"></a>Probar la solución  
 Agregar controles a una hoja de cálculo seleccionándolos en una pestaña personalizada de la cinta de opciones. Cuando guarde la hoja de cálculo, se quitarán estos controles.  
  
### <a name="to-test-the-solution"></a>Para probar la solución.  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  Seleccione cualquier celda de Hoja1.  
  
3.  Haga clic en la pestaña **Complementos** .  
  
4.  En el **group1** grupo, haga clic en **botón**.  
  
     Se mostrará un botón en la celda seleccionada.  
  
5.  Seleccione otra celda en Hoja1.  
  
6.  En el **group1** grupo, haga clic en **NamedRange**.  
  
     Se define un rango con nombre para la celda seleccionada.  
  
7.  Seleccione una serie de celdas en Hoja1.  
  
8.  En el **group1** grupo, haga clic en **ListObject**.  
  
     Se agrega un objeto de lista para las celdas seleccionadas.  
  
9. Guarde la hoja de cálculo.  
  
     Los controles que agregó a Hoja1 ya no aparecen.  
  
## <a name="next-steps"></a>Pasos siguientes  
 Puede obtener más información acerca de los controles en proyectos de complemento de Excel de VSTO en este tema:  
  
-   Para obtener información acerca de cómo guardar controles en una hoja de cálculo, vea el VSTO de Excel complemento dinámica los controles de ejemplo en [tutoriales y ejemplos de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Excel](../vsto/excel-solutions.md)   
 [Los controles de información general sobre documentos de Office de formularios de Windows forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [NamedRange (control)](../vsto/namedrange-control.md)   
 [ListObject (control)](../vsto/listobject-control.md)  
