---
title: Panel Agregar acciones a documentos de Word o libros de Excel
description: Aprenda que para agregar un panel de acciones a un documento Microsoft Office Word o un libro de Microsoft Excel, primero debe crear un Windows Forms control de usuario.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9cf079727581b9cec4b6cb77a0a0c3f0b503b3a0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825529"
---
# <a name="how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks"></a>Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel
  Para agregar un panel de acciones a un Microsoft Office de Word o un libro de Microsoft Excel, primero cree un Windows Forms control de usuario. A continuación, agregue el control de usuario a la propiedad del campo <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` (Word) o `ThisWorkbook.ActionsPane` campo (Excel) del proyecto.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="creating-the-user-control"></a>Crear el control de usuario
 En el procedimiento siguiente se muestra cómo crear el control de usuario en un proyecto de Word o Excel. También agrega un botón al control de usuario que escribe texto en el documento o libro cuando se hace clic en él.

#### <a name="to-create-the-user-control"></a>Para crear el control de usuario

1. Abra el proyecto de nivel de documento de Word o Excel en Visual Studio.

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el **cuadro de diálogo Agregar nuevo** elemento, seleccione Control del **panel** Acciones, así mismo dele el **nombre HelloControl** y haga clic en **Agregar.**

    > [!NOTE]
    > También puede agregar un elemento **control de usuario** al proyecto. Las clases generadas por los **elementos Control del panel Acciones** y **Control** de usuario son funcionalmente equivalentes.

4. En la **Windows Forms** del cuadro de **herramientas,** arrastre un control **Botón** al control .

    > [!NOTE]
    > Si el control no está visible en el diseñador, haga doble clic **en HelloControl** **en Explorador de soluciones**.

5. Agregue el código al controlador <xref:System.Windows.Forms.Control.Click> de eventos del botón. En el ejemplo siguiente se muestra el código de un Microsoft Office de Word.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/HelloControl.vb" id="Snippet12":::

6. En C#, debe agregar un controlador de eventos para el clic de botón. Puede colocar este código en el `HelloControl` constructor después de llamar a `InitializeComponent` .

     Para obtener información sobre cómo crear controladores de eventos, [vea Cómo: Crear controladores de eventos en proyectos de Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/HelloControl.cs" id="Snippet13":::

## <a name="add-the-user-control-to-the-actions-pane"></a>Agregar el control de usuario al panel de acciones
 Para mostrar el panel de acciones, agregue el control de usuario a la propiedad del campo <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> `ThisDocument.ActionsPane` (Word) o `ThisWorkbook.ActionsPane` del campo (Excel).

### <a name="to-add-the-user-control-to-the-actions-pane"></a>Para agregar el control de usuario al panel de acciones

1. Agregue el código siguiente a la `ThisDocument` clase o como una declaración de nivel de clase `ThisWorkbook` (no agregue este código a un método ).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet14":::

2. Agregue el código siguiente al controlador `ThisDocument_Startup` de eventos de la clase o al controlador de eventos de la clase `ThisDocument` `ThisWorkbook_Startup` `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet15":::

## <a name="see-also"></a>Consulte también
- [Información general del panel Acciones](../vsto/actions-pane-overview.md)
- [Tutorial: Insertar texto en un documento desde un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Cómo: Administrar el diseño del control en los paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Tutorial: Insertar texto en un documento desde un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
