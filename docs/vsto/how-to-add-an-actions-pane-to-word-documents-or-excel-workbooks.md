---
title: 'Cómo: agregar un panel de acciones a documentos de Word o libros de Excel'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ebf4896411a46b2c75edd8216bd61623bc9b728f
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548562"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel
  Para agregar un panel de acciones a un documento de Microsoft Office Word o un libro de Microsoft Excel, primero cree un control de usuario de formularios Windows Forms. A continuación, agregue el control de usuario para la <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propiedad de la `ThisDocument.ActionsPane` campo (Word) o `ThisWorkbook.ActionsPane` campo (Excel) en el proyecto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="creating-the-user-control"></a>Crear el control de usuario  
 El siguiente procedimiento muestra cómo crear el control de usuario en una palabra o un proyecto de Excel. También agrega un botón al control de usuario que escribe texto en el documento o libro cuando se hace clic en.  
  
#### <a name="to-create-the-user-control"></a>Para crear el control de usuario  
  
1.  Abra el proyecto de nivel de documento de Word o Excel en Visual Studio.  
  
2.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
3.  En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **Control del panel de acciones**, asígnele el nombre **HelloControl**y haga clic en **agregar**.  
  
    > [!NOTE]  
    >  Alternativamente, puede agregar un **Control de usuario** elemento al proyecto. Las clases generadas por el **Control del panel de acciones** y **Control de usuario** elementos son funcionalmente equivalentes.  
  
4.  Desde el **formularios Windows Forms** pestaña de la **cuadro de herramientas,** arrastre un **botón** control en el control.  
  
    > [!NOTE]  
    >  Si el control no está visible en el diseñador, haga doble clic en **HelloControl** en **el Explorador de soluciones**.  
  
5.  Agregue el código para el <xref:System.Windows.Forms.Control.Click> controlador de eventos del botón. En el ejemplo siguiente se muestra el código de un documento de Microsoft Office Word.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#12)]
     [!code-vb[Trin_VstcoreActionsPaneWord#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb#12)]  
  
6.  En C#, debe agregar un controlador de eventos para el clic de botón. Puede colocar este código en el `HelloControl` constructor después de llamar a `IntializeComponent`.  
  
     Para obtener información sobre cómo crear controladores de eventos, vea [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs#13)]  
  
## <a name="add-the-user-control-to-the-actions-pane"></a>Agregar el control de usuario al panel de acciones  
 Para mostrar el panel Acciones, agregue el control de usuario para la <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> propiedad de la `ThisDocument.ActionsPane` campo (Word) o `ThisWorkbook.ActionsPane` campo (Excel).  
  
### <a name="to-add-the-user-control-to-the-actions-pane"></a>Para agregar el control de usuario al panel de acciones  
  
1.  Agregue el código siguiente a la `ThisDocument` o `ThisWorkbook` clase como una declaración de nivel de clase (no agregue este código a un método).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#14)]
     [!code-vb[Trin_VstcoreActionsPaneWord#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#14)]  
  
2.  Agregue el código siguiente a la `ThisDocument_Startup` controlador de eventos de la `ThisDocument` clase o la `ThisWorkbook_Startup` controlador de eventos de la `ThisWorkbook` clase.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreActionsPaneWord#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#15)]  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Tutorial: Insertar texto en un documento de un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Cómo: administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Tutorial: Insertar texto en un documento de un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  