---
title: Procedimiento Contenido de agregar controles a documentos de Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 10ca0276eb6ddd392fc1ac4e584f5d9caf12fde8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905285"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Procedimiento Contenido de agregar controles a documentos de Word
  En los proyectos de nivel de documento Word, puede agregar controles de contenido al documento en el proyecto en tiempo de diseño o en tiempo de ejecución. En los proyectos de complemento VSTO de Word, puede agregar controles de contenido a cualquier documento abierto en tiempo de ejecución.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 En este tema se describen las tareas siguientes:  
  
- [Agregar controles de contenido en tiempo de diseño](#designtime)  
  
- [Agregar controles de contenido en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)  
  
- [Agregar controles de contenido en tiempo de ejecución en un proyecto de complemento VSTO](#runtimeaddin)  
  
  Para obtener información acerca de los controles de contenido, consulte [controles de contenido](../vsto/content-controls.md).  
  
##  <a name="designtime"></a> Agregar contenido de los controles en tiempo de diseño  
 Hay varias maneras de agregar controles de contenido al documento en un proyecto de nivel de documento en tiempo de diseño:  
  
- Agregar un control de contenido desde la pestaña **Controles de Word** del **Cuadro de herramientas**.  
  
- Agregar un control de contenido en el documento de la misma manera en que se agregaría un control de contenido nativo en Word.  
  
- Arrastrar un control de contenido a un documento desde la ventana **Orígenes de datos** . Esto es útil cuando se desea enlazar el control a los datos al crear el control. Para obtener más información, vea [Cómo: Rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md) y [Cómo: Rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Para agregar un control de contenido a un documento mediante el cuadro de herramientas  
  
1.  En el documento que se hospeda en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , coloque el cursor donde desea agregar el control de contenido o seleccione el texto que desea que el control de contenido reemplace.  
  
2.  Abra el **Cuadro de herramientas** y haga clic en la pestaña **Controles de Word** .  
  
3.  Agregue el control de una de las siguientes formas:  
  
    -   Haga doble clic en un control de contenido en el **Cuadro de herramientas**.  
  
         o  
  
    -   Haga clic en un control de contenido en el **cuadro de herramientas** y, a continuación, presione el **ENTRAR** clave.  
  
         o  
  
    -   Arrastre el control de contenido del **Cuadro de herramientas** al documento. El control de contenido se agrega en la selección actual del documento, no en la ubicación del puntero del mouse.  
  
> [!NOTE]  
>  No se puede agregar un <xref:Microsoft.Office.Tools.Word.GroupContentControl> mediante el **Cuadro de herramientas**. Solo se puede agregar un <xref:Microsoft.Office.Tools.Word.GroupContentControl> en Word o en tiempo de ejecución.  
  
> [!NOTE]  
>  Visual Studio no proporciona un control de contenido de casilla en el cuadro de herramientas. Para agregar un control de contenido de casilla al documento, debe crear un objeto <xref:Microsoft.Office.Tools.Word.ContentControl> mediante programación. Para obtener más información, consulte [controles de contenido](../vsto/content-controls.md).  
  
#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Para agregar un control de contenido a un documento en Word  
  
1.  En el documento que se hospeda en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , coloque el cursor donde desea agregar el control de contenido o seleccione el texto que desea que el control de contenido reemplace.  
  
2.  En la cinta de opciones, haga clic en la pestaña **Desarrollador** .  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, vea [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  En el grupo **Controles** , haga clic en el icono del control de contenido que desea agregar.  
  
##  <a name="runtimedoclevel"></a> Agregar controles de contenido en tiempo de ejecución en un proyecto de nivel de documento  
 Puede agregar controles de contenido mediante programación al documento en tiempo de ejecución mediante el uso de métodos de la <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> propiedad de la `ThisDocument` clase del proyecto. Cada método tiene tres sobrecargas que puede usar para agregar un control de contenido de las maneras siguientes:  
  
- Agregar un control en la selección actual.  
  
- Agregar un control en un intervalo especificado.  
  
- Agregar un control basado en un control de contenido nativo del documento.  
  
  Los controles de contenido creados dinámicamente no se conservan en el documento cuando se cierra. Sin embargo, en el documento permanece un control de contenido nativo. Puede volver a crear un control de contenido basado en un control de contenido nativo la próxima vez que se abra el documento. Para obtener más información, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
> [!NOTE]  
>  Para agregar un control de contenido de casilla a un documento en un proyecto de Word 2010, debe crear un objeto <xref:Microsoft.Office.Tools.Word.ContentControl> . Para obtener más información, consulte [controles de contenido](../vsto/content-controls.md).  
  
### <a name="to-add-a-content-control-at-the-current-selection"></a>Para agregar un control de contenido en la selección actual  
  
1.  Use un <xref:Microsoft.Office.Tools.Word.ControlCollection> método que tiene el nombre `Add` \< *clase del control*> (donde *clase control* es el nombre de clase del control de contenido que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), y que tiene un solo parámetro para el nombre del nuevo control.  
  
     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para agregar un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> al principio del documento. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `AddRichTextControlAtSelection` desde el controlador de eventos `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]  
  
### <a name="to-add-a-content-control-at-a-specified-range"></a>Para agregar un control de contenido en un intervalo especificado  
  
1.  Use un <xref:Microsoft.Office.Tools.Word.ControlCollection> método que tiene el nombre `Add` \< *clase del control*> (donde *clase control* es el nombre de la clase de control de contenido que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), y que tenga un <xref:Microsoft.Office.Interop.Word.Range> parámetro.  
  
     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para agregar un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> al principio del documento. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `AddRichTextControlAtRange` desde el controlador de eventos `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]  
  
### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Para agregar un control de contenido basado en un control de contenido nativo  
  
1.  Use un <xref:Microsoft.Office.Tools.Word.ControlCollection> método que tiene el nombre `Add` \< *clase del control*> (donde *clase control* es el nombre de la clase de control de contenido que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), y que tenga un `Microsoft.Office.Interop.Word.ContentControl` parámetro.  
  
     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para crear un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> para cada control de texto enriquecido nativo que contenga el documento. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `CreateRichTextControlsFromNativeControls` desde el controlador de eventos `ThisDocument_Startup` .  
  
     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> Agregar controles de contenido en tiempo de ejecución en un proyecto de complemento VSTO  
 Puede agregar controles de contenido mediante programación a cualquier documento abierto en tiempo de ejecución mediante un complemento de VSTO. Para ello, genere un elemento host <xref:Microsoft.Office.Tools.Word.Document> basado en un documento abierto y, a continuación, use métodos de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de este elemento host. Cada método tiene tres sobrecargas que puede usar para agregar un control de contenido de las maneras siguientes:  
  
- Agregar un control en la selección actual.  
  
- Agregar un control en un intervalo especificado.  
  
- Agregar un control basado en un control de contenido nativo del documento.  
  
  Los controles de contenido creados dinámicamente no se conservan en el documento cuando se cierra. Sin embargo, en el documento permanece un control de contenido nativo. Puede volver a crear un control de contenido basado en un control de contenido nativo la próxima vez que se abra el documento. Para obtener más información, consulte [Guardar controles dinámicos en documentos de Office](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
  Para obtener más información sobre cómo generar elementos host en proyectos de complemento VSTO, consulte [documentos ampliar Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
> [!NOTE]  
>  Para agregar un control de contenido de casilla a un documento, debe crear un objeto <xref:Microsoft.Office.Tools.Word.ContentControl> . Para obtener más información, consulte [controles de contenido](../vsto/content-controls.md).  
  
### <a name="to-add-a-content-control-at-the-current-selection"></a>Para agregar un control de contenido en la selección actual  
  
1.  Use un <xref:Microsoft.Office.Tools.Word.ControlCollection> método que tiene el nombre `Add` \< *clase del control*> (donde *clase control* es el nombre de clase del control de contenido que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), y que tiene un solo parámetro para el nombre del nuevo control.  
  
     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para agregar un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> al principio del documento activo. Para ejecutar este código, agregue el código a la clase `ThisAddIn` del proyecto y llame al método `AddRichTextControlAtSelection` desde el controlador de eventos `ThisAddIn_Startup` .  
  
     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]  
  
### <a name="to-add-a-content-control-at-a-specified-range"></a>Para agregar un control de contenido en un intervalo especificado  
  
1.  Use un <xref:Microsoft.Office.Tools.Word.ControlCollection> método que tiene el nombre `Add` \< *clase del control*> (donde *clase control* es el nombre de la clase de control de contenido que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), y que tenga un <xref:Microsoft.Office.Interop.Word.Range> parámetro.  
  
     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para agregar un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> al principio del documento activo. Para ejecutar este código, agregue el código a la clase `ThisAddIn` del proyecto y llame al método `AddRichTextControlAtRange` desde el controlador de eventos `ThisAddIn_Startup` .  
  
     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]  
  
#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Para agregar un control de contenido basado en un control de contenido nativo  
  
1.  Use un <xref:Microsoft.Office.Tools.Word.ControlCollection> método que tiene el nombre `Add` \< *clase del control*> (donde *clase control* es el nombre de la clase de control de contenido que desea agregar, como <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), y que tenga un `Microsoft.Office.Interop.Word.ContentControl` parámetro.  
  
     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para crear un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> para cada control de texto enriquecido nativo que contenga el documento, después de que se abra el documento. Para ejecutar este código, agregue el código para a la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]  
  
     En C#, también debe asociar el controlador de eventos `Application_DocumentOpen` al evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]  
  
## <a name="see-also"></a>Vea también  
 [Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Programar complementos VSTO](../vsto/programming-vsto-add-ins.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)  
