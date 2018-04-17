---
title: 'Cómo: agregar controles NamedRange a hojas de cálculo | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fff4299b694dacd00d5f32adced3ef5a6a10f1c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Cómo: Agregar controles NamedRange a hojas de cálculo
  Puede agregar controles <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo de Microsoft Office Excel en tiempo de diseño y en tiempo de ejecución, en los proyectos de nivel de documento.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 También puede agregar controles <xref:Microsoft.Office.Tools.Excel.NamedRange> en tiempo de ejecución a los proyectos de complementos VSTO.  
  
 En este tema se describen las tareas siguientes:  
  
-   [Agregar controles NamedRange en tiempo de diseño](#designtime)  
  
-   [Agregar controles NamedRange en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)  
  
-   [Agregar controles NamedRange en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)  
  
 Para obtener más información sobre los controles <xref:Microsoft.Office.Tools.Excel.NamedRange> , consulte [NamedRange Control](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a> Adding NamedRange Controls at Design Time  
 Existen varias maneras de agregar controles <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo en un proyecto de nivel de documento en tiempo de diseño: desde Excel, desde el **Cuadro de Herramientas**de Visual Studio y desde la ventana **Orígenes de datos** .  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Para agregar un control NamedRange a una hoja de cálculo usando el cuadro de nombre en Excel  
  
1.  Seleccione las celdas que quiere incluir en el rango con nombre.  
  
2.  En el **cuadro de nombres**, escriba un nombre para el rango y presione ENTRAR.  
  
     El **cuadro de nombre** s está situado al lado de la barra de fórmulas, justo sobre la columna **A** de la hoja de cálculo.  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Para agregar un control NamedRange a una hoja de cálculo con el cuadro de herramientas  
  
1.  Abra el **Cuadro de herramientas** y haga clic en la pestaña **Controles de Excel** .  
  
2.  Haga clic en <xref:Microsoft.Office.Tools.Excel.NamedRange> y arrástrelo a una hoja de cálculo.  
  
     Aparece el cuadro de diálogo **Agregar rango con nombre** .  
  
3.  Seleccione las celdas que quiere incluir en el rango con nombre.  
  
4.  Haga clic en **Aceptar**.  
  
     Si no quiere usar el nombre predeterminado que se le ha dado al control puede cambiarlo en la ventana **Propiedades** .  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Para agregar un control NamedRange a una hoja de cálculo con la ventana Orígenes de datos  
  
1.  Abra la ventana **Orígenes de datos** y cree un origen de datos para su proyecto. Para obtener más información, consulte [agregar nuevas conexiones](../data-tools/add-new-connections.md).  
  
2.  Arrastre un único campo desde la ventana **Orígenes de datos** hasta su hoja de cálculo.  
  
     Un control <xref:Microsoft.Office.Tools.Excel.NamedRange> enlazado a los datos se agrega a la hoja de cálculo. Para obtener más información, consulta [Data Binding and Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Adding NamedRange Controls at Run Time in a Document-Level Project  
 Puede agregar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> mediante programación a la hoja de cálculo en tiempo de ejecución. Esto le permite crear los controles host en respuesta a eventos. Los rangos con nombre creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando esta se cierra. Para obtener más información, consulta [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Para agregar un control NamedRange a una hoja de cálculo mediante programación  
  
1.  En el controlador de eventos <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, inserte el siguiente código para agregar el control <xref:Microsoft.Office.Tools.Excel.NamedRange> a la celda **A1** y establezca su propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> en `Hello world!`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> Adding NamedRange Controls at Run Time in an VSTO Add-in project  
 Puede agregar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> mediante programación a cualquier hoja de cálculo abierta de un proyecto de complemento VSTO. Los rangos con nombre creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando esta se cierra. Para obtener más información, consulta [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Para agregar un control NamedRange a una hoja de cálculo mediante programación  
  
1.  El siguiente código crea un elemento host de hoja de cálculo que se basa en la hoja de cálculo abierta; a continuación, agrega un control <xref:Microsoft.Office.Tools.Excel.NamedRange> a la celda **A1** y establece su propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> en `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Vea también  
 [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [NamedRange (Control)](../vsto/namedrange-control.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Cómo: cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  