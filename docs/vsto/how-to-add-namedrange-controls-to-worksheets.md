---
title: 'Cómo: agregar controles NamedRange a hojas de cálculo'
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
ms.openlocfilehash: 35febfa4c4d13b3f5d3d279f7d1c35e96051d54b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867122"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Cómo: agregar controles NamedRange a hojas de cálculo
  Puede agregar <xref:Microsoft.Office.Tools.Excel.NamedRange> controles a una hoja de cálculo de Microsoft Office Excel en tiempo de diseño y en tiempo de ejecución en los proyectos de nivel de documento.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 También puede agregar <xref:Microsoft.Office.Tools.Excel.NamedRange> controles en tiempo de ejecución en los proyectos de complemento VSTO.  
  
 En este tema se describen las tareas siguientes:  
  
- [Agregar controles NamedRange en tiempo de diseño](#designtime)  
  
- [Agregar controles NamedRange en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)  
  
- [Agregar controles NamedRange en tiempo de ejecución en un proyecto de complemento VSTO](#runtimeaddin)  
  
  Para obtener más información acerca de <xref:Microsoft.Office.Tools.Excel.NamedRange> los controles, vea [control NamedRange](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a> Agregar controles NamedRange en tiempo de diseño  
 Existen varias maneras de agregar controles <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo en un proyecto de nivel de documento en tiempo de diseño: desde Excel, desde el **Cuadro de Herramientas**de Visual Studio y desde la ventana **Orígenes de datos** .  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Para agregar un control NamedRange a una hoja de cálculo usando el cuadro de nombre en Excel  
  
1.  Seleccione las celdas que quiere incluir en el rango con nombre.  
  
2.  En el **cuadro nombre**, escriba un nombre para el rango y presione **ENTRAR**.  
  
     El **cuadro de nombre** s está situado al lado de la barra de fórmulas, justo sobre la columna **A** de la hoja de cálculo.  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Para agregar un control NamedRange a una hoja de cálculo con el cuadro de herramientas  
  
1.  Abra el **Cuadro de herramientas** y haga clic en la pestaña **Controles de Excel** .  
  
2.  Haga clic en <xref:Microsoft.Office.Tools.Excel.NamedRange> y arrástrelo a una hoja de cálculo.  
  
     Aparece el cuadro de diálogo **Agregar rango con nombre** .  
  
3.  Seleccione las celdas que quiere incluir en el rango con nombre.  
  
4.  Haga clic en **Aceptar**.  
  
     Si no quiere usar el nombre predeterminado que se le ha dado al control puede cambiarlo en la ventana **Propiedades** .  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Para agregar un control NamedRange a una hoja de cálculo con la ventana Orígenes de datos  
  
1.  Abra la ventana **Orígenes de datos** y cree un origen de datos para su proyecto. Para obtener más información, consulte [agregar nuevas conexiones](../data-tools/add-new-connections.md).  
  
2.  Arrastre un único campo desde la ventana **Orígenes de datos** hasta su hoja de cálculo.  
  
     Un control <xref:Microsoft.Office.Tools.Excel.NamedRange> enlazado a los datos se agrega a la hoja de cálculo. Para obtener más información, consulte [enlace de datos y Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
##  <a name="runtimedoclevel"></a> Agregar controles NamedRange en tiempo de ejecución en un proyecto de nivel de documento  
 Puede agregar un <xref:Microsoft.Office.Tools.Excel.NamedRange> control mediante programación a la hoja de cálculo en tiempo de ejecución. Esto le permite crear los controles host en respuesta a eventos. Los rangos con nombre creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando esta se cierra. Para obtener más información, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Para agregar un control NamedRange a una hoja de cálculo mediante programación  
  
1.  En el controlador de eventos <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, inserte el siguiente código para agregar el control <xref:Microsoft.Office.Tools.Excel.NamedRange> a la celda **A1** y establezca su propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> en `Hello world!`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> Agregar controles NamedRange en tiempo de ejecución en un proyecto de complemento VSTO  
 Puede agregar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> mediante programación a cualquier hoja de cálculo abierta de un proyecto de complemento de VSTO. Los rangos con nombre creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando esta se cierra. Para obtener más información, consulte [documentos ampliar Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Para agregar un control NamedRange a una hoja de cálculo mediante programación  
  
1.  El siguiente código crea un elemento host de hoja de cálculo que se basa en la hoja de cálculo abierta; a continuación, agrega un control <xref:Microsoft.Office.Tools.Excel.NamedRange> a la celda **A1** y establece su propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> en `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Vea también  
 [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [NamedRange (control)](../vsto/namedrange-control.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Cómo: cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  