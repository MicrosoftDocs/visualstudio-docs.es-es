---
title: Agregar controles a un documento en tiempo de ejecución en el complemento de VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e8cde57ece3774e94f923387e1a8f7ca71cf797
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254172"
---
# <a name="walkthrough-add-controls-to-a-document-at-run-time-in-a-vsto-add-in"></a>Tutorial: Agregar controles a un documento en tiempo de ejecución en un complemento de VSTO
  Puede Agregar controles a cualquier documento de Word Microsoft Office abierto mediante un complemento de VSTO. En este tutorial se muestra cómo usar la cinta para permitir a los usuarios <xref:Microsoft.Office.Tools.Word.Controls.Button> agregar un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> o un a un documento.

 **Se aplica a:** La información de este tema se aplica a los proyectos de complemento de VSTO para Word 2010. Para obtener más información, consulta [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).

 En este tutorial se muestran las tareas siguientes:

- Crear un nuevo proyecto de complemento de VSTO de Word.

- Proporcionar una interfaz de usuario (UI) para agregar controles al documento.

- Agregar controles al documento en tiempo de ejecución.

- Quitar controles del documento.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Requisitos previos
 Necesita los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-word-add-in-project"></a>Crear un nuevo proyecto de complemento de Word
 Empiece creando un proyecto de complemento de VSTO de Word.

### <a name="to-create-a-new-word-vsto-add-in-project"></a>Para crear un nuevo proyecto de complemento de VSTO de Word

1. Cree un proyecto de complemento de VSTO para Word con el nombre **WordDynamicControls**. Para obtener más información, vea [Cómo: Cree proyectos de Office en Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

2. Agregue una referencia al ensamblado **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** . Esta referencia es obligatoria para agregar mediante programación un control de Windows Forms al documento más adelante en este tutorial.

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>Proporcionar una interfaz de usuario para agregar controles a un documento
 Agregue una pestaña personalizada a la cinta en Word. Los usuarios pueden seleccionar las casillas en la pestaña para agregar controles a un documento.

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Para proporcionar una interfaz de usuario para agregar controles a un documento

1. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

2. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Cinta (diseñador visual)** .

3. Cambie el nombre de la nueva cinta de opciones por **MyRibbon**y haga clic en **Agregar**.

    El archivo **MyRibbon.cs** o **MyRibbon.vb** se abre en el diseñador de la cinta de opciones y muestra una ficha y un grupo predeterminados.

4. En el diseñador de la cinta, haga clic en el grupo **group1** .

5. En la ventana **Propiedades** , cambie la propiedad **Etiqueta** para **group1** a **Agregar controles**.

6. Desde la pestaña **Controles de la cinta de Office** del **Cuadro de herramientas**, arrastre un control **CheckBox** a **group1**.

7. Haga clic en **CheckBox1** para seleccionarlo.

8. En la ventana **Propiedades** , cambie las siguientes propiedades:

   | Propiedad. | Valor |
   |-----------|-----------------------|
   | **Name** | **addButtonCheckBox** |
   | **Etiqueta** | **Botón Agregar** |

9. Agregue una segunda casilla a **group1**, y, a continuación, cambie las siguientes propiedades.

   | Property | Valor |
   |-----------|---------------------------|
   | **Name** | **addRichTextCheckBox** |
   | **Label** | **Agregar control de texto enriquecido** |

10. En el diseñador de la cinta, haga doble clic en **Agregar botón**.

     El controlador de eventos <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> de la casilla **Agregar botón** se abre en el Editor de código.

11. Vuelva al diseñador de la cinta y haga doble clic en **Agregar control de texto enriquecido**.

     El controlador de eventos <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> de la casilla **Agregar control de texto enriquecido** se abre en el Editor de código.

    Más adelante en este tutorial, agregará código a estos controladores de eventos para agregar y quitar controles en el documento activo.

## <a name="add-and-remove-controls-on-the-active-document"></a>Agregar y quitar controles en el documento activo
 En el código de complemento de VSTO, debe convertir el documento activo en un <xref:Microsoft.Office.Tools.Word.Document>*de* para poder agregar un control. En soluciones de Office, pueden agregarse controles administrados solo a los elementos host, que actúan como contenedores para los controles. En los proyectos de complemento de VSTO, se pueden crear elementos host en tiempo de ejecución mediante `GetVstoObject` el método.

 Agregue métodos a la clase `ThisAddIn` que se puedan llamar para agregar o quitar un <xref:Microsoft.Office.Tools.Word.Controls.Button> o <xref:Microsoft.Office.Tools.Word.RichTextContentControl> en el documento activo. Más adelante en este tutorial, llamará a estos métodos desde los controladores de eventos <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> de las casillas en la cinta.

### <a name="to-add-and-remove-controls-on-the-active-document"></a>Para agregar y quitar controles en el documento activo

1. En **Explorador de soluciones**, haga doble clic en *ThisAddIn.CS* o *ThisAddIn. VB* para abrir el archivo en el editor de código.

2. Agregue el código siguiente a la clase `ThisAddIn` . Este código declara los objetos <xref:Microsoft.Office.Tools.Word.Controls.Button> y <xref:Microsoft.Office.Tools.Word.RichTextContentControl> que representan los controles que se agregarán al documento.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]

3. Agregue el método siguiente a la clase `ThisAddIn`. Cuando el usuario hace clic en la casilla **Agregar botón** en la cinta, este método agrega un <xref:Microsoft.Office.Tools.Word.Controls.Button> a la selección actual en el documento si la casilla está activada, o quita el <xref:Microsoft.Office.Tools.Word.Controls.Button> si la casilla está desactivada.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]

4. Agregue el método siguiente a la clase `ThisAddIn`. Cuando el usuario hace clic en la casilla **Agregar control de texto enriquecido** en la cinta, este método agrega un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> a la selección actual en el documento si la casilla está activada, o quita el <xref:Microsoft.Office.Tools.Word.RichTextContentControl> si la casilla está desactivada.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]

## <a name="remove-the-button-control-when-the-document-is-saved"></a>Quitar el control de botón cuando se guarda el documento
 Los controles de formularios de Windows Forms no se conservan cuando se guarda y se cierra el documento. Sin embargo, un contenedor de ActiveX para cada control permanece en el documento, y el borde de este contenedor lo pueden ver los usuarios finales cuando se vuelve a abrir el documento. Hay varias maneras de limpiar los controles de formularios de Windows Forms creados dinámicamente en complementos de VSTO. En este tutorial, se quita mediante programación el control <xref:Microsoft.Office.Tools.Word.Controls.Button> cuando se guarda el documento.

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Para quitar el control Button cuando el documento se guarda

1. En el archivo de código *ThisAddIn.CS* o *ThisAddIn. VB* , agregue el método siguiente a `ThisAddIn` la clase. Este método es un controlador de eventos para el evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> . Si el documento tiene un elemento host <xref:Microsoft.Office.Tools.Word.Document> que está asociado a él, el controlador de eventos obtiene el elemento host y quita el control <xref:Microsoft.Office.Tools.Word.Controls.Button> , si existe.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]

2. En C#, agregue el código siguiente al controlador de eventos `ThisAddIn_Startup` . Este código es necesario en C# para conectar el controlador de eventos `Application_DocumentBeforeSave` con el evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> .

     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Agregar y quitar controles cuando el usuario hace clic en las casillas de la cinta de opciones
 Por último, modifique <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> los controladores de eventos de las casillas que agregó a la cinta para agregar o quitar controles en el documento.

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Para agregar o quitar controles cuando el usuario hace clic en las casillas de la cinta de opciones

1. En el archivo de código *MyRibbon.CS* o *myribbon. VB* , reemplace los controladores `addButtonCheckBox_Click` de `addRichTextCheckBox_Click` eventos y generados por el código siguiente. Este código vuelve a definir estos controladores de eventos para llamar a los métodos `ToggleButtonOnDocument` y `ToggleRichTextControlOnDocument` que ha agregado a la clase `ThisAddIn` anteriormente en este tutorial.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]

## <a name="test-the-solution"></a>Prueba de la solución
 Agregue controles a un documento seleccionándolos en la pestaña personalizada de la cinta. Al guardar el documento, el control <xref:Microsoft.Office.Tools.Word.Controls.Button> se quita.

### <a name="to-test-the-solution"></a>Para probar la solución.

1. Presione **F5** para ejecutar el proyecto.

2. En el documento activo, presione **entrar** varias veces para agregar nuevos párrafos vacíos al documento.

3. Seleccione el primer párrafo.

4. Haga clic en la pestaña **Complementos** .

5. En el grupo **Agregar controles** , haga clic en **Agregar botón**.

     Se mostrará un botón en el primer párrafo.

6. Seleccione el último párrafo.

7. En el grupo **Agregar controles** , haga clic en **Agregar control de texto enriquecido**.

     Se agregará un control de contenido de texto enriquecido al último párrafo.

8. Guarde el documento.

     El botón se quitará del documento.

## <a name="next-steps"></a>Pasos siguientes
 Puede obtener más información acerca de los controles en los complementos de VSTO en estos temas:

- Para obtener un ejemplo que muestra cómo agregar muchos otros tipos de controles a un documento en tiempo de ejecución y volver a crear los controles cuando se vuelve a abrir el documento, vea el ejemplo de controles dinámicos de complementos de Word en los [ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).

- Para ver un tutorial que muestra cómo agregar controles a una hoja de cálculo mediante un complemento de VSTO para Excel, vea [Tutorial: Agregar controles a una hoja de cálculo en tiempo de ejecución en el proyecto](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)de complemento de VSTO.

## <a name="see-also"></a>Vea también
- [Soluciones de Word](../vsto/word-solutions.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Conservar controles dinámicos en documentos de Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Cómo: Agregar controles Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Cómo: Agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
