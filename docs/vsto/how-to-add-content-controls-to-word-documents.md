---
title: 'Cómo: Agregar controles de contenido a documentos de Word'
description: Obtenga información sobre que, en los proyectos de Word de nivel de documento, puede agregar controles de contenido al documento en el proyecto en tiempo de diseño o en tiempo de ejecución.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a902e85f8c53aa7a3d1ebe3b6480a7c68fa60601
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827908"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Cómo: Agregar controles de contenido a documentos de Word
  En proyectos de Word de nivel de documento, puede agregar controles de contenido al documento en el proyecto en tiempo de diseño o en tiempo de ejecución. En proyectos de complemento de VSTO de Word, puede agregar controles de contenido a cualquier documento abierto en tiempo de ejecución.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 En este tema se describen las tareas siguientes:

- [Agregar controles de contenido en tiempo de diseño](#designtime)

- [Agregar controles de contenido en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)

- [Agregar controles de contenido en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)

  Para obtener información sobre los controles de contenido, vea [Controles de contenido](../vsto/content-controls.md).

## <a name="add-content-controls-at-design-time"></a><a name="designtime"></a> Agregar controles de contenido en tiempo de diseño
 Hay varias maneras de agregar controles de contenido al documento en un proyecto de nivel de documento en tiempo de diseño:

- Agregar un control de contenido desde la pestaña **Controles de Word** del **Cuadro de herramientas**.

- Agregar un control de contenido en el documento de la misma manera en que se agregaría un control de contenido nativo en Word.

- Arrastrar un control de contenido a un documento desde la ventana **Orígenes de datos** . Esto es útil cuando se desea enlazar el control a los datos al crear el control. Para obtener más información, [vea Cómo: Rellenar](../vsto/how-to-populate-documents-with-data-from-objects.md) documentos con datos de objetos y [Cómo:](../vsto/how-to-populate-documents-with-data-from-a-database.md)Rellenar documentos con datos de una base de datos .

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Para agregar un control de contenido a un documento mediante el cuadro de herramientas

1. En el documento que se hospeda en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , coloque el cursor donde desea agregar el control de contenido o seleccione el texto que desea que el control de contenido reemplace.

2. Abra el **Cuadro de herramientas** y haga clic en la pestaña **Controles de Word** .

3. Agregue el control de una de las siguientes formas:

    - Haga doble clic en un control de contenido en el **Cuadro de herramientas**.

         or

    - Haga clic en un control de contenido en el **cuadro de herramientas** y presione la **tecla** Entrar.

         or

    - Arrastre el control de contenido del **Cuadro de herramientas** al documento. El control de contenido se agrega en la selección actual del documento, no en la ubicación del puntero del mouse.

> [!NOTE]
> No se puede agregar un <xref:Microsoft.Office.Tools.Word.GroupContentControl> mediante el **Cuadro de herramientas**. Solo se puede agregar un <xref:Microsoft.Office.Tools.Word.GroupContentControl> en Word o en tiempo de ejecución.

> [!NOTE]
> Visual Studio no proporciona un control de contenido de casilla en el cuadro de herramientas. Para agregar un control de contenido de casilla al documento, debe crear un objeto <xref:Microsoft.Office.Tools.Word.ContentControl> mediante programación. Para obtener más información, vea [Controles de contenido.](../vsto/content-controls.md)

#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Para agregar un control de contenido a un documento en Word

1. En el documento que se hospeda en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , coloque el cursor donde desea agregar el control de contenido o seleccione el texto que desea que el control de contenido reemplace.

2. En la cinta de opciones, haga clic en la pestaña **Desarrollador** .

    > [!NOTE]
    > Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, [vea Cómo: Mostrar la pestaña Desarrollador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. En el grupo **Controles** , haga clic en el icono del control de contenido que desea agregar.

## <a name="add-content-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Agregar controles de contenido en tiempo de ejecución en un proyecto de nivel de documento
 Puede agregar controles de contenido mediante programación al documento en tiempo de ejecución con métodos de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de la clase `ThisDocument` en el proyecto. Cada método tiene tres sobrecargas que puede usar para agregar un control de contenido de las maneras siguientes:

- Agregar un control en la selección actual.

- Agregar un control en un intervalo especificado.

- Agregar un control basado en un control de contenido nativo del documento.

  Los controles de contenido creados dinámicamente no se conservan en el documento cuando se cierra. Sin embargo, en el documento permanece un control de contenido nativo. Puede volver a crear un control de contenido basado en un control de contenido nativo la próxima vez que se abra el documento. Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución.](../vsto/adding-controls-to-office-documents-at-run-time.md)

> [!NOTE]
> Para agregar un control de contenido de casilla a un documento en un proyecto de Word 2010, debe crear un objeto <xref:Microsoft.Office.Tools.Word.ContentControl> . Para obtener más información, vea [Controles de contenido.](../vsto/content-controls.md)

### <a name="to-add-a-content-control-at-the-current-selection"></a>Para agregar un control de contenido en la selección actual

1. Use un método que tenga el nombre (donde clase de control es el nombre de clase del control de contenido que desea agregar, como ) y que tenga un único parámetro para el nombre del <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> nuevo  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> control.

     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para agregar un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> al principio del documento. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `AddRichTextControlAtSelection` desde el controlador de eventos `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet700":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet700":::

### <a name="to-add-a-content-control-at-a-specified-range"></a>Para agregar un control de contenido en un intervalo especificado

1. Use un método que tenga el nombre (donde clase de control es el nombre de la clase de control de contenido que desea agregar, como ) y <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> que tenga un  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> parámetro <xref:Microsoft.Office.Interop.Word.Range> .

     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para agregar un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> al principio del documento. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `AddRichTextControlAtRange` desde el controlador de eventos `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet701":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet701":::

### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Para agregar un control de contenido basado en un control de contenido nativo

1. Use un método que tenga el nombre (donde clase de control es el nombre de la clase de control de contenido que desea agregar, como ) y <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> que tenga un  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> parámetro `Microsoft.Office.Interop.Word.ContentControl` .

     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para crear un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> para cada control de texto enriquecido nativo que contenga el documento. Para ejecutar este código, agregue el código a la clase `ThisDocument` del proyecto y llame al método `CreateRichTextControlsFromNativeControls` desde el controlador de eventos `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet702":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet702":::

## <a name="add-content-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Agregar controles de contenido en tiempo de ejecución en un proyecto de complemento de VSTO
 Puede agregar controles de contenido mediante programación a cualquier documento abierto en tiempo de ejecución a través de un complemento de VSTO. Para ello, genere un elemento host <xref:Microsoft.Office.Tools.Word.Document> basado en un documento abierto y, a continuación, use métodos de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de este elemento host. Cada método tiene tres sobrecargas que puede usar para agregar un control de contenido de las maneras siguientes:

- Agregar un control en la selección actual.

- Agregar un control en un intervalo especificado.

- Agregar un control basado en un control de contenido nativo del documento.

  Los controles de contenido creados dinámicamente no se conservan en el documento cuando se cierra. Sin embargo, en el documento permanece un control de contenido nativo. Puede volver a crear un control de contenido basado en un control de contenido nativo la próxima vez que se abra el documento. Para obtener más información, vea [Conservar controles dinámicos en documentos de Office.](../vsto/persisting-dynamic-controls-in-office-documents.md)

  Para obtener más información sobre cómo generar elementos host en proyectos de complemento de VSTO, vea Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo [de ejecución.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

> [!NOTE]
> Para agregar un control de contenido de casilla a un documento, debe crear un objeto <xref:Microsoft.Office.Tools.Word.ContentControl> . Para obtener más información, vea [Controles de contenido.](../vsto/content-controls.md)

### <a name="to-add-a-content-control-at-the-current-selection"></a>Para agregar un control de contenido en la selección actual

1. Use un método que tenga el nombre (donde clase de control es el nombre de clase del control de contenido que desea agregar, como ) y que tenga un único parámetro para el nombre del <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> nuevo  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> control.

     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para agregar un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> al principio del documento activo. Para ejecutar este código, agregue el código a la clase `ThisAddIn` del proyecto y llame al método `AddRichTextControlAtSelection` desde el controlador de eventos `ThisAddIn_Startup` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet1":::

### <a name="to-add-a-content-control-at-a-specified-range"></a>Para agregar un control de contenido en un intervalo especificado

1. Use un método que tenga el nombre (donde clase de control es el nombre de la clase de control de contenido que desea agregar, como ) y <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> que tenga un  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> parámetro <xref:Microsoft.Office.Interop.Word.Range> .

     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para agregar un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> al principio del documento activo. Para ejecutar este código, agregue el código a la clase `ThisAddIn` del proyecto y llame al método `AddRichTextControlAtRange` desde el controlador de eventos `ThisAddIn_Startup` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet2":::

#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Para agregar un control de contenido basado en un control de contenido nativo

1. Use un método que tenga el nombre (donde clase de control es el nombre de la clase de control de contenido que desea agregar, como ) y <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> que tenga un  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> parámetro `Microsoft.Office.Interop.Word.ContentControl` .

     El siguiente ejemplo de código usa el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> para crear un nuevo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> para cada control de texto enriquecido nativo que contenga el documento, después de que se abra el documento. Para ejecutar este código, agregue el código para a la clase `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet3":::

     En C#, también debe asociar el controlador de eventos `Application_DocumentOpen` al evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet6":::

## <a name="see-also"></a>Consulte también
- [Automatización de Word mediante objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitaciones de programación de los elementos host y los controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Programación de complementos VSTO](../vsto/programming-vsto-add-ins.md)
- [Personalizaciones de nivel de documento del programa](../vsto/programming-document-level-customizations.md)
