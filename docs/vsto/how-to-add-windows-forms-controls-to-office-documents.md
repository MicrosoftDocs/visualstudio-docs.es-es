---
title: "C&#243;mo: Agregar controles de Windows Forms a documentos de Office | Microsoft Docs"
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
  - "controles [desarrollo de Office en Visual Studio], controles de Windows Forms"
  - "documentos [desarrollo de Office en Visual Studio], controles de Windows Forms"
  - "documentos de Office [desarrollo de Office en Visual Studio], controles de Windows Forms"
  - "controles de formularios Windows Forms [desarrollo de Office en Visual Studio], agregar"
ms.assetid: 4d188ad2-8e17-4eb0-8422-2ff56c683e3d
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# C&#243;mo: Agregar controles de Windows Forms a documentos de Office
  Puede agregar controles de Windows Forms a documentos de Microsoft Office Excel y Microsoft Office Word en tiempo de diseño en proyectos de nivel de documento.  En tiempo de ejecución, puede agregar controles en personalizaciones de nivel de documento y en complementos de VSTO.  Por ejemplo, puede agregar un control <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> a la hoja de cálculo para que los usuarios puedan seleccionar una de las opciones de una lista.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 En este tema se describen las tareas siguientes:  
  
-   [Agregar controles en tiempo de diseño](#designtime)  
  
-   [Agregar controles en tiempo de ejecución en proyectos de nivel de documento](#runtimedoclevel)  
  
-   [Agregar controles en tiempo de ejecución en complementos de VSTO](#runtimeaddin)  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Para ver una demostración en vídeo relacionada, consulte [Cómo: Agregar controles a una superficie de documento en tiempo de ejecución](http://go.microsoft.com/fwlink/?LinkId=132782).  
  
##  <a name="designtime"></a> Agregar controles en tiempo de diseño  
 Hay varias maneras de agregar controles de Windows Forms al documento en un proyecto de nivel de documento en tiempo de diseño.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Para arrastrar un control de Windows Forms al documento  
  
1.  Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador.  Para obtener más información, consulte el artículo [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En la pestaña **Controles comunes** del **Cuadro de herramientas**, haga clic en el control que desee agregar y arrástrelo hasta el documento.  
  
    > [!NOTE]  
    >  Cuando seleccione un control en Excel, verá **\=EMBED\("WinForms.Control.Host",""\)** en la **Barra de fórmulas**.  Este texto es necesario y no se debe eliminar.  
  
#### Para dibujar un control de Windows Forms en el documento  
  
1.  Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador.  Para obtener más información, consulte el artículo [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En la ficha **Controles comunes** del **Cuadro de herramientas**, haga clic en el control que desea agregar.  
  
3.  En el documento, haga clic en el punto en que desee que se encuentre la esquina superior izquierda del control y arrastre hasta donde desee que se encuentre la esquina inferior derecha del control.  
  
     El control se agregará al documento con la ubicación y el tamaño especificados.  
  
    > [!NOTE]  
    >  Cuando seleccione un control en Excel, verá **\=EMBED\("WinForms.Control.Host",""\)** en la **Barra de fórmulas**.  Este texto es necesario y no se debe eliminar.  
  
#### Para agregar un control de Windows Forms mediante un clic en el control  
  
1.  Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador.  Para obtener más información, consulte el artículo [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En la pestaña **Controles comunes** del **Cuadro de herramientas**, haga clic en el control que desea agregar.  
  
3.  En el documento, haga clic en el lugar en el que desea agregar el control.  
  
     El control se agrega al documento con el tamaño predeterminado.  
  
    > [!NOTE]  
    >  Cuando seleccione un control en Excel, verá **\=EMBED\("WinForms.Control.Host",""\)** en la **Barra de fórmulas**.  Este texto es necesario y no se debe eliminar.  
  
#### Para agregar un control de Windows Forms al documento mediante un doble clic en el control  
  
1.  Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador.  Para obtener más información, consulte el artículo [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En la pestaña **Controles comunes** del **Cuadro de herramientas**, haga doble clic en el control que desea agregar.  
  
     El control se agrega al documento en el centro del documento o del panel activo.  
  
    > [!NOTE]  
    >  Cuando seleccione un control en Excel, verá **\=EMBED\("WinForms.Control.Host",""\)** en la **Barra de fórmulas**.  Este texto es necesario y no se debe eliminar.  
  
#### Para agregar un control de Windows Forms al documento mediante la tecla ENTRAR  
  
1.  Cree o abra un proyecto de libro de Excel o un proyecto de documento de Word en Visual Studio para que el documento esté visible en el diseñador.  Para obtener más información, consulte el artículo [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En la pestaña **Controles comunes** del **Cuadro de herramientas**, haga clic en el control que desee agregar y presione la tecla ENTRAR.  
  
     El control se agrega al documento en el centro del documento o del panel activo.  
  
    > [!NOTE]  
    >  Cuando seleccione un control en Excel, verá **\=EMBED\("WinForms.Control.Host",""\)** en la **Barra de fórmulas**.  Este texto es necesario y no se debe eliminar.  
  
##  <a name="runtimedoclevel"></a> Agregar controles en tiempo de ejecución en proyectos de nivel de documento  
 Puede agregar controles de Windows Forms mediante programación a documentos en tiempo de ejecución.  En Word, use los métodos de la propiedad <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> de la clase `ThisDocument`.  En Excel, use los métodos de la propiedad <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> de una clase `Sheet`*n*.  Cada método tiene varias sobrecargas que permiten especificar la ubicación del control de maneras diferentes.  
  
 Cuando se agrega un control de Windows Forms a un documento en tiempo de ejecución, el control no se conserva en el documento cuando éste se cierra.   Puede volver a crear el control la próxima vez que se abra el documento.  Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Para agregar un control de Windows Forms en tiempo de ejecución  
  
1.  Use un método con el nombre Add\<*control class*\> \(donde *control class* es el nombre de clase del control de Windows Forms que se desea agregar, como, por ejemplo, <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>\).  
  
     En el siguiente ejemplo de código se muestra cómo agregar un <xref:Microsoft.Office.Tools.Excel.Controls.Button> a la celda **C5** de `Sheet1` en un proyecto de nivel de documento para Excel.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#4)]  
  
##  <a name="runtimeaddin"></a> Agregar controles en tiempo de ejecución en complementos de VSTO  
 Puede agregar controles de Windows Forms mediante programación a cualquier documento abierto en tiempo de ejecución.  En primer lugar, genere un elemento host que se base en una hoja de cálculo o documento abierto.  A continuación, en Word, use los métodos de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> del nuevo elemento host.  En Excel, use los métodos de la propiedad <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> del nuevo elemento host.  Cada método tiene varias sobrecargas que permiten especificar la ubicación del control de maneras diferentes.  
  
 Cuando se agrega un control de Windows Forms a un documento en tiempo de ejecución, el control no se conserva en el documento cuando éste se cierra.   Puede volver a crear el control la próxima vez que se abra el documento.  Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
 Para obtener más información sobre cómo generar elementos host en proyectos de complemento de VSTO, consulte [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Para agregar un control de Windows Forms en tiempo de ejecución  
  
1.  Use un método con el nombre Add\<*control class*\> \(donde *control class* es el nombre de clase del control de Windows Forms que se desea agregar, como, por ejemplo, <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>\).  
  
    > [!NOTE]  
    >  En proyectos de complemento de VSTO que tengan como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, debe agregar una referencia al ensamblado Microsoft.Office.Tools.Excel.v4.0.Utilities.dll o Microsoft.Office.Tools.Word.v4.0.Utilities.dll antes de poder acceder a los métodos Add\<*control class*\>.  
  
     En el siguiente ejemplo de código se muestra cómo agregar un <xref:Microsoft.Office.Tools.Word.Controls.Button> al primer párrafo del documento activo usando un complemento de VSTO de Word.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDynamicControls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#7)]  
  
## Vea también  
 [Información general sobre controles de formularios Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Cómo: Cambiar el tamaño de controles en celdas de hojas de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  