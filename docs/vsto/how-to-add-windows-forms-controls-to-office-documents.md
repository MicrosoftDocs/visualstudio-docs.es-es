---
title: 'Cómo: agregar controles de Windows forms a documentos de Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6fcff642f75da15f649cc7e3ab525b4db0ac1c83
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264552"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Cómo: agregar controles de formularios Windows Forms a documentos de Office
  Puede agregar controles de Windows Forms a documentos de Microsoft Office Excel y Microsoft Office Word en tiempo de diseño en proyectos de nivel de documento. En tiempo de ejecución, puede agregar controles en personalizaciones de nivel de documento y complementos de VSTO. Por ejemplo, puede agregar un control <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> a la hoja de cálculo para que los usuarios puedan seleccionar una de las opciones de una lista.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 En este tema se describen las tareas siguientes:  
  
-   [Agregar controles en tiempo de diseño](#designtime)  
  
-   [Agregar controles en tiempo de ejecución en proyectos de nivel de documento](#runtimedoclevel)  
  
-   [Agregar controles en tiempo de ejecución en complementos VSTO](#runtimeaddin)  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [cómo expuesta los I: agregar controles a un documento en tiempo de ejecución?](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a> Agregar controles en tiempo de diseño  
 Hay varias maneras de agregar controles de Windows Forms al documento en un proyecto de nivel de documento en tiempo de diseño.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Para arrastrar un control de Windows Forms al documento  
  
1.  Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: proyectos de Office crear en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En el **controles comunes** pestaña de la **cuadro de herramientas**, haga clic en el control que desea agregar y arrástrelo al documento.  
  
    > [!NOTE]  
    >  Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.  
  
### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Para dibujar un control de Windows Forms en el documento  
  
1.  Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: proyectos de Office crear en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En el **controles comunes** pestaña de la **cuadro de herramientas**, haga clic en el control que desea agregar.  
  
3.  En el documento, haga clic en el punto en que desee que se encuentre la esquina superior izquierda del control y arrastre hasta donde desee que se encuentre la esquina inferior derecha del control.  
  
     El control se agregará al documento con la ubicación y el tamaño especificados.  
  
    > [!NOTE]  
    >  Cuando se selecciona un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en el **barra de fórmulas**. Este texto es necesario y no se debe eliminar.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Para agregar un control de Windows Forms mediante un clic en el control  
  
1.  Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: proyectos de Office crear en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En el **controles comunes** pestaña de la **cuadro de herramientas**, haga clic en el control que desea agregar  
  
3.  En el documento, haga clic en el lugar en el que desea agregar el control.  
  
     El control se agrega al documento con el tamaño predeterminado.  
  
    > [!NOTE]  
    >  Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Para agregar un control de Windows Forms al documento mediante un doble clic en el control  
  
1.  Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: proyectos de Office crear en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En el **controles comunes** pestaña de la **cuadro de herramientas**, haga doble clic en el control que desea agregar.  
  
     El control se agrega al documento en el centro del documento o del panel activo.  
  
    > [!NOTE]  
    >  Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.  
  
### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Para agregar un control de formularios Windows Forms al documento presionando la tecla ENTRAR  
  
1.  Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En el **controles comunes** pestaña de la **cuadro de herramientas**, haga clic en el control que desea agregar y presione la **ENTRAR** clave.  
  
     El control se agrega al documento en el centro del documento o del panel activo.  
  
    > [!NOTE]  
    >  Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.  
  
##  <a name="runtimedoclevel"></a> Agregar controles en tiempo de ejecución en proyectos de nivel de documento  
 Puede agregar mediante programación controles de formularios Windows Forms a un documento en tiempo de ejecución. En Word, use los métodos de la propiedad <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> de la clase `ThisDocument`. En Excel, use los métodos de la <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> propiedad de un `Sheet` *n* clase. Cada método tiene varias sobrecargas que permiten especificar la ubicación del control de maneras diferentes.  
  
 Cuando se agrega un control de formularios Windows Forms a un documento en tiempo de ejecución, el control no se conserva en el documento cuando se cierra el documento. Puede volver a crear el control la próxima vez que se abra el documento. Para obtener más información, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>Para agregar un control de formularios Windows Forms en tiempo de ejecución  
  
1.  Usar un método que tiene el nombre del complemento\<*clase control*> (donde *clase control* es el nombre de clase del control de formularios Windows Forms que se desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
     En el ejemplo de código siguiente se muestra cómo agregar un <xref:Microsoft.Office.Tools.Excel.Controls.Button> a la celda **C5** de `Sheet1` en un proyecto de nivel de documento para Excel.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]  
  
##  <a name="runtimeaddin"></a> Agregar controles en tiempo de ejecución en complementos VSTO  
 Puede agregar controles de formularios Windows Forms mediante programación a cualquier documento abierto en tiempo de ejecución. En primer lugar, genere un elemento host que se base en una hoja de cálculo o documento abierto. A continuación, en Word, use los métodos de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> del nuevo elemento host. En Excel, use los métodos de la propiedad <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> del nuevo elemento host. Cada método tiene varias sobrecargas que permiten especificar la ubicación del control de maneras diferentes.  
  
 Cuando se agrega un control de formularios Windows Forms a un documento en tiempo de ejecución, el control no se conserva en el documento cuando se cierra el documento. Puede volver a crear el control la próxima vez que se abra el documento. Para obtener más información, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Para obtener más información sobre cómo generar elementos host en proyectos de complemento de VSTO, consulte [documentos de Word extender y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-add-a-windows-forms-control-at-runtime"></a>Para agregar un control de formularios Windows Forms en tiempo de ejecución  
  
1.  Usar un método que tiene el nombre del complemento\<*clase control*> (donde *clase control* es el nombre de clase del control de formularios Windows Forms que se desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>).  
  
    > [!NOTE]  
    >  En el complemento de VSTO los proyectos que tienen como destino el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, debe agregar una referencia a la *ensamblado Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* o *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* ensamblado antes de poder acceder el complemento\<*clase control*> métodos.  
  
     En el siguiente ejemplo de código se muestra cómo agregar un <xref:Microsoft.Office.Tools.Word.Controls.Button> al primer párrafo del documento activo usando un complemento de VSTO de Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]  
  
## <a name="see-also"></a>Vea también  
 [Controles de formularios Windows Forms en información general acerca de documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Cómo: cambiar el tamaño de controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  