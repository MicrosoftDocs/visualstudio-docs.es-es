---
title: 'Cómo: agregar controles Bookmark a documentos de Word'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: de5868674790239b8374ef9796308280588ae96e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547256"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Cómo: agregar controles Bookmark a documentos de Word
  En proyectos de nivel de documento, puede agregar controles <xref:Microsoft.Office.Tools.Word.Bookmark> al documento en el proyecto en tiempo de diseño o en tiempo de ejecución. En proyectos de complemento VSTO, puede agregar controles <xref:Microsoft.Office.Tools.Word.Bookmark> a cualquier documento abierto en tiempo de ejecución.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 En este tema se describen las tareas siguientes:

- [Agregar controles Bookmark en tiempo de diseño](#designtime)

- [Agregar controles Bookmark en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)

- [Agregar controles Bookmark en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)

  Para obtener más información sobre <xref:Microsoft.Office.Tools.Word.Bookmark> los controles, vea [Bookmark (control](../vsto/bookmark-control.md)).

## <a name="add-bookmark-controls-at-design-time"></a><a name="designtime"></a>Agregar controles Bookmark en tiempo de diseño
 Hay varias maneras de agregar controles <xref:Microsoft.Office.Tools.Word.Bookmark> al documento en un proyecto de nivel de documento en tiempo de diseño:

- Desde el **Cuadro de herramientas**de Visual Studio.

   Puede arrastrar el control <xref:Microsoft.Office.Tools.Word.Bookmark> desde el **Cuadro de herramientas** hasta su documento. Este método es recomendable si ya está usando el **Cuadro de herramientas** para agregar controles de Windows Forms al documento.

- Desde dentro de Word.

   Puede agregar el control <xref:Microsoft.Office.Tools.Word.Bookmark> al documento de la misma manera que agregaría el marcador nativo. La ventaja de agregarlo de esta manera es que puede asignarle el nombre al control al crearlo.

- Desde la ventana **Orígenes de datos** .

   Puede arrastrar el control <xref:Microsoft.Office.Tools.Word.Bookmark> a su documento desde la ventana **Orígenes de datos** . Esto es útil cuando se desea enlazar el control a los datos al mismo tiempo. Puede agregar el control host de la misma manera que agregaría un control de Windows Forms desde la ventana **Orígenes de datos** . Para obtener más información, consulte [enlace de datos y Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Para agregar un control Bookmark a un documento desde el Cuadro de herramientas

1. Abra el **Cuadro de herramientas** y haga clic en la pestaña **Controles de Word** .

2. Arrastre un control <xref:Microsoft.Office.Tools.Word.Bookmark> al documento.

     Aparecerá el cuadro de diálogo **Agregar marcador** .

3. Seleccione el texto u otros elementos que desee incluir en el marcador.

4. Haga clic en **Aceptar**.

     Si no desea conservar el nombre de marcador predeterminado, puede cambiar el nombre en la ventana **Propiedades** .

#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Para agregar un control Bookmark a un documento en Word

1. En el documento que se hospeda en el diseñador de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , coloque el cursor donde desea agregar el marcador o seleccione el texto que desea que contenga el marcador.

2. En la pestaña **Insertar** de la cinta, en el grupo **Vínculos** , haga clic en el botón **Marcador** .

3. En el cuadro de diálogo **Marcador** , escriba el nombre del nuevo marcador y haga clic en **Agregar**.

## <a name="add-bookmark-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a>Agregar controles Bookmark en tiempo de ejecución en un proyecto de nivel de documento
 Puede agregar controles <xref:Microsoft.Office.Tools.Word.Bookmark> mediante programación al documento en tiempo de ejecución con métodos de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de la clase `ThisDocument` en el proyecto. Hay dos sobrecargas de método que puede usar para agregar un control <xref:Microsoft.Office.Tools.Word.Bookmark> de las maneras siguientes:

- Agregar un <xref:Microsoft.Office.Tools.Word.Bookmark> en un intervalo especificado.

- Agregar un <xref:Microsoft.Office.Tools.Word.Bookmark> que se base en un marcador nativo del documento (es decir, un <xref:Microsoft.Office.Interop.Word.Bookmark>).

  Los controles <xref:Microsoft.Office.Tools.Word.Bookmark> creados de forma dinámica no se conservan en el documento cuando se cierra. Sin embargo, un <xref:Microsoft.Office.Interop.Word.Bookmark> nativo permanece en el documento. Puede volver a crear un control <xref:Microsoft.Office.Tools.Word.Bookmark> que se base en un marcador nativo la próxima vez que se abra el documento. Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Para agregar un control Bookmark mediante programación a un documento

1. En el controlador de eventos `ThisDocument_Startup` de su proyecto, inserte el siguiente código para agregar el control <xref:Microsoft.Office.Tools.Word.Bookmark> al primer párrafo del documento.

     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]

    > [!NOTE]
    > Si desea crear un control <xref:Microsoft.Office.Tools.Word.Bookmark> desde un <xref:Microsoft.Office.Interop.Word.Bookmark>existente, use el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> y pase el <xref:Microsoft.Office.Interop.Word.Bookmark>existente.

## <a name="add-bookmark-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>Agregar controles Bookmark en tiempo de ejecución en un proyecto de complemento de VSTO
 Puede agregar controles <xref:Microsoft.Office.Tools.Word.Bookmark> mediante programación a cualquier documento abierto en tiempo de ejecución a través de un complemento de VSTO. Para ello, genere un elemento host <xref:Microsoft.Office.Tools.Word.Document> basado en un documento abierto y, a continuación, use métodos de la propiedad <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> de este elemento host. Hay dos sobrecargas de método que puede usar para agregar un control <xref:Microsoft.Office.Tools.Word.Bookmark> de las maneras siguientes:

- Agregar un <xref:Microsoft.Office.Tools.Word.Bookmark> en un intervalo especificado.

- Agregar un <xref:Microsoft.Office.Tools.Word.Bookmark> que se base en un marcador nativo del documento (es decir, un <xref:Microsoft.Office.Interop.Word.Bookmark>).

  Los controles <xref:Microsoft.Office.Tools.Word.Bookmark> creados de forma dinámica no se conservan en el documento cuando se cierra. Sin embargo, un <xref:Microsoft.Office.Interop.Word.Bookmark> nativo permanece en el documento. Puede volver a crear un control <xref:Microsoft.Office.Tools.Word.Bookmark> que se base en un marcador nativo la próxima vez que se abra el documento. Para obtener más información, vea [conservar controles dinámicos en documentos de Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

  Para obtener más información sobre cómo generar elementos host en proyectos de complemento de VSTO, vea [ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Para agregar un control Bookmark en un intervalo especificado

1. Use el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> y pase el <xref:Microsoft.Office.Interop.Word.Range> donde desea agregar el <xref:Microsoft.Office.Tools.Word.Bookmark>.

     El siguiente ejemplo de código agrega un nuevo <xref:Microsoft.Office.Tools.Word.Bookmark> al principio del documento activo. Para usar este ejemplo, ejecute el código del controlador de eventos `ThisAddIn_Startup` en un proyecto de complemento de VSTO de Word.

     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]

#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Para agregar un control Bookmark que se base en un control Bookmark nativo

1. Use el método <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> y pase el <xref:Microsoft.Office.Interop.Word.Bookmark> existente que desee usar como base para el nuevo <xref:Microsoft.Office.Tools.Word.Bookmark>.

     En el siguiente ejemplo de código se crea un nuevo <xref:Microsoft.Office.Tools.Word.Bookmark> que se basa en el primer <xref:Microsoft.Office.Interop.Word.Bookmark> del documento activo. Para usar este ejemplo, ejecute el código del controlador de eventos `ThisAddIn_Startup` en un proyecto de complemento de VSTO de Word.

     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]

## <a name="see-also"></a>Consulte también
- [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)
- [Personalizaciones de nivel de documento de programa](../vsto/programming-document-level-customizations.md)
- [Cómo: cambiar el tamaño de los controles Bookmark](../vsto/how-to-resize-bookmark-controls.md)
