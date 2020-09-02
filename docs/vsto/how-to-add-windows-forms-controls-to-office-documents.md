---
title: 'Cómo: agregar controles de Windows Forms a documentos de Office'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b12d51ffe3a2e647a067b95d320e8beb70cac384
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547542"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Cómo: agregar controles Windows Forms a documentos de Office
  Puede agregar controles de Windows Forms a documentos de Microsoft Office Excel y Microsoft Office Word en tiempo de diseño en proyectos de nivel de documento. En tiempo de ejecución, puede Agregar controles en las personalizaciones de nivel de documento y en los complementos de VSTO. Por ejemplo, puede Agregar un <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> control a la hoja de cálculo para que los usuarios puedan seleccionarlo en una lista de opciones.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 En este tema se describen las tareas siguientes:

- [Agregar controles en tiempo de diseño](#designtime)

- [Agregar controles en tiempo de ejecución en proyectos de nivel de documento](#runtimedoclevel)

- [Agregar controles en tiempo de ejecución en complementos de VSTO](#runtimeaddin)

## <a name="add-controls-at-design-time"></a><a name="designtime"></a> Agregar controles en tiempo de diseño
 Hay varias maneras de agregar controles de Windows Forms al documento en un proyecto de nivel de documento en tiempo de diseño.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Para arrastrar un control de Windows Forms al documento

1. Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. En la pestaña **controles comunes** del **cuadro de herramientas**, haga clic en el control que desee agregar y arrástrelo hasta el documento.

    > [!NOTE]
    > Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Para dibujar un control de Windows Forms en el documento

1. Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. En la pestaña **controles comunes** del **cuadro de herramientas**, haga clic en el control que desea agregar.

3. En el documento, haga clic en el punto en que desee que se encuentre la esquina superior izquierda del control y arrastre hasta donde desee que se encuentre la esquina inferior derecha del control.

     El control se agregará al documento con la ubicación y el tamaño especificados.

    > [!NOTE]
    > Al seleccionar un control en Excel, verá **= embed ("WinForms. control. host", "")**  en la **barra de fórmulas**. Este texto es necesario y no se debe eliminar.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Para agregar un control de Windows Forms mediante un clic en el control

1. Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. En la pestaña **controles comunes** del **cuadro de herramientas**, haga clic en el control que desea agregar.

3. En el documento, haga clic en el lugar en el que desea agregar el control.

     El control se agrega al documento con el tamaño predeterminado.

    > [!NOTE]
    > Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Para agregar un control de Windows Forms al documento mediante un doble clic en el control

1. Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. En la pestaña **controles comunes** del **cuadro de herramientas**, haga doble clic en el control que desea agregar.

     El control se agrega al documento en el centro del documento o del panel activo.

    > [!NOTE]
    > Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Para agregar un control de Windows Forms al documento presionando la tecla entrar

1. Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador. Para obtener información sobre cómo crear proyectos, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. En la pestaña **controles comunes** del **cuadro de herramientas**, haga clic en el control que desee agregar y presione la tecla **entrar** .

     El control se agrega al documento en el centro del documento o del panel activo.

    > [!NOTE]
    > Cuando seleccione un control en Excel, verá **=EMBED("WinForms.Control.Host","")** en la **Barra de fórmulas**. Este texto es necesario y no se debe eliminar.

## <a name="add-controls-at-run-time-in-document-level-projects"></a><a name="runtimedoclevel"></a> Agregar controles en tiempo de ejecución en proyectos de nivel de documento
 Puede agregar controles de Windows Forms mediante programación a documentos en tiempo de ejecución. En Word, use los métodos de la propiedad <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> de la clase `ThisDocument`. En Excel, use los métodos de la <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> propiedad de una `Sheet` clase *n* . Cada método tiene varias sobrecargas que permiten especificar la ubicación del control de maneras diferentes.

 Cuando se agrega un control de Windows Forms a un documento en tiempo de ejecución, el control no se conserva en el documento cuando éste se cierra.  Puede volver a crear el control la próxima vez que se abra el documento. Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Para agregar un control de Windows Forms en tiempo de ejecución

1. Use un método que tenga el nombre Add \<*control class*> (donde *control Class* es el nombre de clase del control Windows Forms que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

     En el ejemplo de código siguiente se muestra cómo agregar una <xref:Microsoft.Office.Tools.Excel.Controls.Button> a la celda **C5** de `Sheet1` en un proyecto de nivel de documento para Excel.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]

## <a name="add-controls-at-run-time-in-vsto-add-ins"></a><a name="runtimeaddin"></a> Agregar controles en tiempo de ejecución en complementos de VSTO
 Puede agregar controles de Windows Forms mediante programación a cualquier documento abierto en tiempo de ejecución. En primer lugar, genere un elemento host que se base en una hoja de cálculo o documento abierto. A continuación, en Word, use los métodos de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> del nuevo elemento host. En Excel, use los métodos de la propiedad <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> del nuevo elemento host. Cada método tiene varias sobrecargas que permiten especificar la ubicación del control de maneras diferentes.

 Cuando se agrega un control de Windows Forms a un documento en tiempo de ejecución, el control no se conserva en el documento cuando éste se cierra.  Puede volver a crear el control la próxima vez que se abra el documento. Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Para obtener más información sobre cómo generar elementos host en proyectos de complemento de VSTO, vea [ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Para agregar un control de Windows Forms en tiempo de ejecución

1. Use un método que tenga el nombre Add \<*control class*> (donde *control Class* es el nombre de clase del control Windows Forms que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

    > [!NOTE]
    > En los proyectos de complemento de VSTO que tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, debe agregar una referencia al *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* o *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* ensamblado antes de poder tener acceso a los \<*control class*> métodos Add.

     En el siguiente ejemplo de código se muestra cómo agregar un <xref:Microsoft.Office.Tools.Word.Controls.Button> al primer párrafo del documento activo usando un complemento de VSTO de Word.

     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]

## <a name="see-also"></a>Consulte también
- [Información general sobre los controles de Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Cómo: cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
