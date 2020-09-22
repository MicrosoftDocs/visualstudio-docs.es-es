---
title: 'Tutorial: insertar texto en un documento desde un panel de acciones'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 61e71f31ce887c7e1ea9ec57b0aa3f24a45be364
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843344"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Tutorial: insertar texto en un documento desde un panel de acciones
  En este tutorial se muestra cómo crear un panel de acciones en un documento de Microsoft Office Word. El panel acciones contiene dos controles que recopilan entradas y, a continuación, envían el texto al documento.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Diseñar una interfaz utilizando Windows Forms controles en un control del panel de acciones.

- Mostrar el panel de acciones cuando se abra la aplicación.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Crear el proyecto
 El primer paso es crear un proyecto de tipo Documento de Word.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de documento de Word con el nombre **mi panel de acciones básicas**. En el asistente, seleccione **crear un nuevo documento**. Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el proyecto **Panel mis acciones básicas** a **Explorador de soluciones**.

## <a name="add-text-and-bookmarks-to-the-document"></a>Agregar texto y marcadores al documento
 El panel acciones enviará texto a los marcadores del documento. Para diseñar el documento, escriba texto para crear un formulario básico.

### <a name="to-add-text-to-your-document"></a>Para agregar texto al documento

1. Escriba el siguiente texto en el documento de Word:

    **21 de marzo de 2008**

    **Nombre**

    **Dirección**

    **Este es un ejemplo de un panel de acciones básicas de Word.**

   Puede Agregar un <xref:Microsoft.Office.Tools.Word.Bookmark> control al documento arrastrándolo desde el cuadro de **herramientas** en Visual Studio o mediante el cuadro de diálogo **marcador** de Word.

### <a name="to-add-a-bookmark-control-to-your-document"></a>Para agregar un control Bookmark a un documento

1. En la pestaña **controles de Word** del **cuadro de herramientas**, arrastre un <xref:Microsoft.Office.Tools.Word.Bookmark> control hasta el documento.

     Aparece el cuadro de diálogo **Agregar control de marcador** .

2. Seleccione el **nombre**de la palabra, sin seleccionar la marca de párrafo, y haga clic en **Aceptar**.

    > [!NOTE]
    > La marca de párrafo debe estar fuera del marcador. Si las marcas de párrafo no están visibles en el documento, haga clic en el menú **herramientas** , elija **Microsoft Office herramientas de Word** y, a continuación, haga clic en **Opciones**. Haga clic en la pestaña **Ver** y active la casilla **marcas de párrafo** en la sección **marcas de formato** del cuadro de diálogo **Opciones** .

3. En la ventana **propiedades** , cambie la propiedad **nombre** de **Bookmark1** a **showName**.

4. Seleccione la palabra **Dirección**, sin seleccionar la marca de párrafo.

5. En la pestaña **Insertar** de la cinta de opciones, en el grupo **vínculos** , haga clic en **marcador**.

6. En el cuadro de diálogo **marcador** , escriba **showAddress** en el cuadro **nombre del marcador** y haga clic en **Agregar**.

## <a name="add-controls-to-the-actions-pane"></a>Agregar controles al panel de acciones
 Para diseñar la interfaz del panel de acciones, agregue un control del panel de acciones al proyecto y, a continuación, agregue Windows Forms controles al control del panel de acciones.

### <a name="to-add-an-actions-pane-control"></a>Para agregar un control del panel de acciones

1. Seleccione el proyecto **Panel mis acciones básicas** en **Explorador de soluciones**.

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , haga clic en el **control panel de acciones**, asigne al control el nombre **InsertTextControl** y haga clic en **Agregar**.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Para agregar controles de Windows Forms al control del panel de acciones

1. Si el control del panel de acciones no está visible en el diseñador, haga doble clic en **InsertTextControl**.

2. En la pestaña **controles comunes** del **cuadro de herramientas**, arrastre un control **etiqueta** al control panel de acciones.

3. Cambie la propiedad **texto** del control etiqueta a **nombre**.

4. Agregue un control de **cuadro de texto** al control del panel de acciones y cambie las siguientes propiedades.

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**getName (**|
    |**Tamaño**|**130, 20**|

5. Agregue un segundo control **etiqueta** al control panel de acciones y cambie la propiedad **texto** a **Dirección**.

6. Agregue un segundo control de **cuadro de texto** al control del panel de acciones y cambie las siguientes propiedades.

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**GetAddress (**|
    |**Acepta la devolución**|**True**|
    |**Multiline**|**True**|
    |**Tamaño**|**130, 40**|

7. Agregue un control **botón** al control panel de acciones y cambie las siguientes propiedades.

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**Dtex**|
    |**Texto**|**Insertar**|

## <a name="add-code-to-insert-text-into-the-document"></a>Agregar código para insertar texto en el documento
 En el panel acciones, escriba código que inserte el texto de los cuadros de texto en los controles adecuados del <xref:Microsoft.Office.Tools.Word.Bookmark> documento. Puede utilizar la `Globals` clase para tener acceso a los controles del documento desde los controles del panel de acciones. Para obtener más información, consulte [acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Para insertar texto del panel de acciones en un marcador del documento

1. Agregue el código siguiente al <xref:System.Windows.Forms.Control.Click> controlador de eventos del botón **addText** .

     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]

2. En C#, debe agregar un controlador de eventos para el clic de botón. Este código se puede colocar en el `InsertTextControl` constructor después de la llamada a `InitializeComponent` . Para obtener información sobre cómo crear controladores de eventos, consulte [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]

## <a name="add-code-to-show-the-actions-pane"></a>Agregar código para mostrar el panel de acciones
 Para mostrar el panel de acciones, agregue el control que creó a la colección de controles.

### <a name="to-show-the-actions-pane"></a>Para mostrar el panel de acciones

1. Cree una nueva instancia del control del panel de acciones en la `ThisDocument` clase.

     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]

2. Agregue el código siguiente al <xref:Microsoft.Office.Tools.Word.Document.Startup> controlador de eventos de `ThisDocument` .

     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]

## <a name="test-the-application"></a>Prueba de la aplicación
 Pruebe el documento para comprobar que el panel de acciones se abre al abrir el documento y que el texto escrito en los cuadros de texto se inserta en los marcadores al hacer clic en el botón.

### <a name="to-test-your-document"></a>Para probar el documento

1. Presione **F5** para ejecutar el proyecto.

2. Confirme que el panel de acciones está visible.

3. Escriba su nombre y dirección en los cuadros de texto del panel acciones y haga clic en **Insertar**.

## <a name="next-steps"></a>Pasos siguientes
 A continuación, podría realizar las siguientes tareas:

- Cree un panel de acciones en Excel. Para obtener más información, vea [Cómo: agregar un panel de acciones a los libros de Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).

- Enlazar datos a controles en un panel de acciones. Para obtener más información, vea [Tutorial: enlazar datos a controles en un panel de acciones de Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

## <a name="see-also"></a>Vea también
- [Información general del panel de acciones](../vsto/actions-pane-overview.md)
- [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Cómo: agregar un panel de acciones a los libros de Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Cómo: administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Bookmark (control)](../vsto/bookmark-control.md)
