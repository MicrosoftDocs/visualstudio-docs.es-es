---
title: "C&#243;mo: Agregar controles de contenido a documentos de Word | Microsoft Docs"
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
  - "permisos restringidos [desarrollo de Office en Visual Studio]"
  - "DropDownListContentControl, agregar a documentos"
  - "BuildingBlockGalleryContentControl, agregar a documentos"
  - "protección parcial de documentos [desarrollo de Office en Visual Studio]"
  - "RichTextContentControl, agregar a documentos"
  - "Word [desarrollo de Office en Visual Studio], protección parcial de documentos "
  - "controles de contenido [desarrollo de Office en Visual Studio], proteger"
  - "PictureContentControl, agregar a documentos"
  - "GroupContentControl, agregar a documentos"
  - "protección de documentos [desarrollo de Office en Visual Studio]"
  - "PlainTextContentControl, agregar a documentos"
  - "controles de contenido [desarrollo de Office en Visual Studio], agregar"
  - "ComboBoxContentControl, agregar a documentos"
  - "DatePickerContentControl, agregar a documentos"
  - "Word [desarrollo de Office en Visual Studio], permisos restringidos"
ms.assetid: 68ddb24e-71c6-46f7-8e11-c9899d7814df
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# C&#243;mo: Agregar controles de contenido a documentos de Word
  En proyectos de Word de nivel de documento, puede agregar controles de contenido al documento en el proyecto en tiempo de diseño o en tiempo de ejecución. En proyectos de complemento de VSTO de Word, puede agregar controles de contenido a cualquier documento abierto en tiempo de ejecución.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 En este tema se describen las tareas siguientes:  
  
-   [Agregar controles de contenido en tiempo de diseño](#designtime)  
  
-   [Agregar controles de contenido en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)  
  
-   [Agregar controles de contenido en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)  
  
 Para más información sobre los controles de contenido, consulte [Controles de contenido](../vsto/content-controls.md).  
  
##  <a name="designtime"></a> Agregar controles de contenido en tiempo de diseño  
 Hay varias maneras de agregar controles de contenido al documento en un proyecto de nivel de documento en tiempo de diseño:  
  
-   Agregar un control de contenido desde la pestaña **Controles de Word** del **Cuadro de herramientas**.  
  
-   Agregar un control de contenido en el documento de la misma manera en que se agregaría un control de contenido nativo en Word.  
  
-   Arrastrar un control de contenido a un documento desde la ventana **Orígenes de datos**. Esto es útil cuando se desea enlazar el control a los datos al crear el control. Para obtener más información, vea [Cómo: Rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md) y [Cómo: Rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Para agregar un control de contenido a un documento mediante el cuadro de herramientas  
  
1.  En el documento que se hospeda en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], coloque el cursor donde desea agregar el control de contenido o seleccione el texto que desea que el control de contenido reemplace.  
  
2.  Abra el **Cuadro de herramientas** y haga clic en la pestaña **Controles de Word**.  
  
3.  Agregue el control de una de las siguientes formas:  
  
    -   Haga doble clic en un control de contenido en el **Cuadro de herramientas**.  
  
         o  
  
    -   Haga clic en un control de contenido en el **Cuadro de herramientas** y, a continuación, presione la tecla ENTRAR.  
  
         o  
  
    -   Arrastre el control de contenido del **Cuadro de herramientas** al documento. El control de contenido se agrega en la selección actual del documento, no en la ubicación del puntero del mouse.  
  
> [!NOTE]  
>  No se puede agregar un <xref:Microsoft.Office.Tools.Word.GroupContentControl> mediante el **Cuadro de herramientas**. Solo se puede agregar un <xref:Microsoft.Office.Tools.Word.GroupContentControl> en Word o en tiempo de ejecución.  
  
> [!NOTE]  
>  Visual Studio no proporciona un control de contenido de casilla en el cuadro de herramientas. Para agregar un control de contenido de casilla al documento, debe crear un objeto <xref:Microsoft.Office.Tools.Word.ContentControl> mediante programación. Para obtener más información, consulta [Controles de contenido](../vsto/content-controls.md).  
  
#### Para agregar un control de contenido a un documento en Word  
  
1.  En el documento que se hospeda en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], coloque el cursor donde desea agregar el control de contenido o seleccione el texto que desea que el control de contenido reemplace.  
  
2.  En la cinta de opciones, haga clic en la pestaña **Desarrollador**.  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulta [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  En el grupo **Controles**, haga clic en el icono del control de contenido que desea agregar.  
  
##  <a name="runtimedoclevel"></a> Agregar controles de contenido en tiempo de ejecución en un proyecto de nivel de documento  
 Puede agregar controles de contenido mediante programación al documento en tiempo de ejecución con métodos de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de la clase `ThisDocument` en el proyecto. Cada método tiene tres sobrecargas que puede usar para agregar un control de contenido de las maneras siguientes:  
  
-   Agregar un control en la selección actual.  
  
-   Agregar un control en un intervalo especificado.  
  
-   Agregar un control basado en un control de contenido nativo del documento.  
  
 Los controles de contenido creados dinámicamente no se conservan en el documento cuando se cierra. Sin embargo, en el documento permanece un control de contenido nativo. Puede volver a crear un control de contenido basado en un control de contenido nativo la próxima vez que se abra el documento. Para obtener más información, consulta [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
> [!NOTE]  
>  Para agregar un control de contenido de casilla a un documento en un proyecto de Word 2010, debe crear un objeto <xref:Microsoft.Office.Tools.Word.ContentControl>. Para obtener más información, consulta [Controles de contenido](../vsto/content-controls.md).  
  
#### Para agregar un control de contenido en la selección actual  
  
1.  Use un método <xref:Microsoft.Office.Tools.Word.ControlCollection> que tenga el nombre `Add`\<*control class*\> \(donde *control class* es el nombre de la clase de control de contenido que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) y que tenga un solo parámetro para el nombre del control nuevo.  
  
     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para agregar un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> al principio del documento. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `AddRichTextControlAtSelection` desde el controlador de eventos `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlReference#700](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#700)]  
  
#### Para agregar un control de contenido en un intervalo especificado  
  
1.  Use un método <xref:Microsoft.Office.Tools.Word.ControlCollection> que tenga el nombre `Add`\<*control class*\> \(donde *control class* es el nombre de la clase de control de contenido que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) y que tenga un parámetro <xref:Microsoft.Office.Interop.Word.Range>.  
  
     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para agregar un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> al principio del documento. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `AddRichTextControlAtRange` desde el controlador de eventos `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlReference#701](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#701)]  
  
#### Para agregar un control de contenido basado en un control de contenido nativo  
  
1.  Use un método <xref:Microsoft.Office.Tools.Word.ControlCollection> que tenga el nombre `Add`\<*control class*\> \(donde *control class* es el nombre de la clase de control de contenido que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) y que tenga un parámetro Microsoft.Office.Interop.Word.ContentControl.  
  
     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para crear un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> para cada control de texto enriquecido nativo que contenga el documento. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `CreateRichTextControlsFromNativeControls` desde el controlador de eventos `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlReference#702](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlReference/CS/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlReference/VB/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> Agregar controles de contenido en tiempo de ejecución en un proyecto de complemento de VSTO  
 Puede agregar controles de contenido mediante programación a cualquier documento abierto en tiempo de ejecución a través de un complemento de VSTO. Para ello, genere un elemento host <xref:Microsoft.Office.Tools.Word.Document> basado en un documento abierto y, a continuación, use métodos de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de este elemento host. Cada método tiene tres sobrecargas que puede usar para agregar un control de contenido de las maneras siguientes:  
  
-   Agregar un control en la selección actual.  
  
-   Agregar un control en un intervalo especificado.  
  
-   Agregar un control basado en un control de contenido nativo del documento.  
  
 Los controles de contenido creados dinámicamente no se conservan en el documento cuando se cierra. Sin embargo, en el documento permanece un control de contenido nativo. Puede volver a crear un control de contenido basado en un control de contenido nativo la próxima vez que se abra el documento. Para obtener más información, consulta [Guardar controles dinámicos en documentos de Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
 Para más información sobre la generación de elementos host en proyectos de complemento de VSTO, consulte [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
> [!NOTE]  
>  Para agregar un control de contenido de casilla a un documento, debe crear un objeto <xref:Microsoft.Office.Tools.Word.ContentControl>. Para obtener más información, consulta [Controles de contenido](../vsto/content-controls.md).  
  
#### Para agregar un control de contenido en la selección actual  
  
1.  Use un método <xref:Microsoft.Office.Tools.Word.ControlCollection> que tenga el nombre `Add`\<*control class*\> \(donde *control class* es el nombre de la clase de control de contenido que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) y que tenga un solo parámetro para el nombre del control nuevo.  
  
     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para agregar un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> al principio del documento activo. Para ejecutar este código, agregue el código a la clase `ThisAddIn` del proyecto y llame al método `AddRichTextControlAtSelection` desde el controlador de eventos `ThisAddIn_Startup`.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDynamicControls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#1)]  
  
#### Para agregar un control de contenido en un intervalo especificado  
  
1.  Use un método <xref:Microsoft.Office.Tools.Word.ControlCollection> que tenga el nombre `Add`\<*control class*\> \(donde *control class* es el nombre de la clase de control de contenido que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) y que tenga un parámetro <xref:Microsoft.Office.Interop.Word.Range>.  
  
     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para agregar un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> al principio del documento activo. Para ejecutar este código, agregue el código a la clase `ThisAddIn` del proyecto y llame al método `AddRichTextControlAtRange` desde el controlador de eventos `ThisAddIn_Startup`.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDynamicControls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#2)]  
  
#### Para agregar un control de contenido basado en un control de contenido nativo  
  
1.  Use un método <xref:Microsoft.Office.Tools.Word.ControlCollection> que tenga el nombre `Add`\<*control class*\> \(donde *control class* es el nombre de la clase de control de contenido que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>\) y que tenga un parámetro Microsoft.Office.Interop.Word.ContentControl.  
  
     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para crear un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> para cada control de texto enriquecido nativo que contenga el documento, después de que se abra el documento. Para ejecutar este código, agregue el código para a la clase `ThisAddIn` del proyecto.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDynamicControls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#3)]  
  
     En C\#, también debe asociar el controlador de eventos `Application_DocumentOpen` al evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#6)]  
  
## Vea también  
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)  
  
  