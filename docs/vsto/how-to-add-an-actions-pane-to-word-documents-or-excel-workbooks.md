---
title: Agregar el panel de acciones a documentos de Word o libros de Excel
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 2d24ec3a17c9e0824c6b7aaffeaaac02c1c4f76e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546229"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel
  Para agregar un panel de acciones a un documento de Microsoft Office Word o a un libro de Microsoft Excel, primero debe crear un control de usuario Windows Forms. A continuación, agregue el control de usuario a la <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propiedad del `ThisDocument.ActionsPane` campo (Word) o el `ThisWorkbook.ActionsPane` campo (Excel) del proyecto.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="creating-the-user-control"></a>Crear el control de usuario
 En el siguiente procedimiento se muestra cómo crear un control de usuario en un proyecto de Word o Excel. También agrega un botón al control de usuario que escribe texto en el documento o libro cuando se hace clic en él.

#### <a name="to-create-the-user-control"></a>Para crear el control de usuario

1. Abra el proyecto de nivel de documento de Word o Excel en Visual Studio.

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **control del panel de acciones**, asígnele el nombre **HelloControl**y haga clic en **Agregar**.

    > [!NOTE]
    > También puede Agregar un elemento de **control de usuario** a su proyecto. Las clases generadas por el **control del panel de acciones** y los elementos de control de **usuario** son funcionalmente equivalentes.

4. En la pestaña **Windows Forms** del **cuadro de herramientas,** arrastre un control de **botón** hasta el control.

    > [!NOTE]
    > Si el control no está visible en el diseñador, haga doble clic en **HelloControl** en **Explorador de soluciones**.

5. Agregue el código al <xref:System.Windows.Forms.Control.Click> controlador de eventos del botón. En el ejemplo siguiente se muestra el código de un documento de Microsoft Office Word.

     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]

6. En C#, debe agregar un controlador de eventos para el clic de botón. Este código se puede colocar en el `HelloControl` constructor después de la llamada a `InitializeComponent` .

     Para obtener información sobre cómo crear controladores de eventos, consulte [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]

## <a name="add-the-user-control-to-the-actions-pane"></a>Agregar el control de usuario al panel de acciones
 Para mostrar el panel de acciones, agregue el control de usuario a la <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propiedad del `ThisDocument.ActionsPane` campo (Word) o el `ThisWorkbook.ActionsPane` campo (Excel).

### <a name="to-add-the-user-control-to-the-actions-pane"></a>Para agregar el control de usuario al panel de acciones

1. Agregue el código siguiente a la `ThisDocument` `ThisWorkbook` clase o como una declaración de nivel de clase (no agregue este código a un método).

     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]

2. Agregue el código siguiente al `ThisDocument_Startup` controlador de eventos de la `ThisDocument` clase o al `ThisWorkbook_Startup` controlador de eventos de la `ThisWorkbook` clase.

     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]

## <a name="see-also"></a>Vea también
- [Información general del panel de acciones](../vsto/actions-pane-overview.md)
- [Tutorial: insertar texto en un documento desde un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Cómo: administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Tutorial: insertar texto en un documento desde un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
