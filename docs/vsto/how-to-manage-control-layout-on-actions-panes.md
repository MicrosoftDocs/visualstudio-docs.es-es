---
title: Procedimiento Administrar el diseño de controles en paneles de acciones
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], control layout
- controls [Office development in Visual Studio], layout on actions panes
- smart documents [Office development in Visual Studio], control layout
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 043f93c12181d34e9d2a92435c854cdf76f18904
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255821"
---
# <a name="how-to-manage-control-layout-on-actions-panes"></a>Procedimiento Administrar el diseño de controles en paneles de acciones
  De forma predeterminada, un panel de acciones se acopla a la derecha de un documento o una hoja de cálculo. sin embargo, se puede acoplar a la izquierda, la parte superior o la parte inferior. Si usa varios controles de usuario, puede escribir código para apilar correctamente los controles de usuario en el panel de acciones. Para obtener más información, vea [información general del panel de acciones](../vsto/actions-pane-overview.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 El orden de apilamiento de los controles depende de si el panel de acciones está acoplado vertical u horizontalmente.

> [!NOTE]
> Si el usuario cambia el tamaño del panel de acciones en tiempo de ejecución, puede establecer que los controles cambien de tamaño con el panel de acciones. Puede utilizar la propiedad <xref:System.Windows.Forms.Control.Anchor%2A> de un control de Windows Forms para anclar los controles al panel de acciones. Para obtener más información, vea [Cómo: Delimite los](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)controles en Windows Forms.

> [!NOTE]
> Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-set-the-stack-order-of-the-actions-pane-controls"></a>Para establecer el orden de apilamiento de los controles del panel de acciones

1. Abra un proyecto de nivel de documento para Microsoft Office Word que incluya un panel de acciones con varios controles de usuario o controles de panel de acciones anidados. Para obtener más información, vea [Cómo: Agregar un panel de acciones a documentos de Word o libros](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)de Excel.

2. Haga clic con el botón secundario en **ThisDocument.CS** o **ThisDocument. VB** en **Explorador de soluciones** y, a continuación, haga clic en **Ver código**.

3. En el <xref:Microsoft.Office.Tools.ActionsPane.OrientationChanged> controlador de eventos del panel de acciones, compruebe si la orientación del panel de acciones es horizontal.

     [!code-csharp[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreActionsPaneWord#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#30)]

4. Si la orientación es horizontal, apile los controles del panel de acciones desde la izquierda; en caso contrario, apilelos desde la parte superior.

     [!code-csharp[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreActionsPaneWord#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#31)]

5. En C#, debe agregar un controlador de eventos para `ActionsPane` al <xref:Microsoft.Office.Tools.Word.Document.Startup> controlador de eventos. Para obtener información acerca de la creación de controladores [de eventos, consulte Cómo: Cree controladores de eventos en proyectos](../vsto/how-to-create-event-handlers-in-office-projects.md)de Office.

     [!code-csharp[Trin_VstcoreActionsPaneWord#32](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#32)]

6. Ejecute el proyecto y compruebe que los controles del panel de acciones están apilados de izquierda a derecha cuando el panel de acciones está acoplado en la parte superior del documento y los controles se apilan de arriba a abajo cuando el panel de acciones se acopla en el lado derecho del documento.

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#29)]
 [!code-vb[Trin_VstcoreActionsPaneWord#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#29)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo se necesita:

- Proyecto de nivel de documento de Word con un panel de acciones que contiene varios controles de usuario o controles de panel de acciones anidados.

## <a name="see-also"></a>Vea también
- [Información general del panel de acciones](../vsto/actions-pane-overview.md)
- [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Tutorial: Insertar texto en un documento desde un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Tutorial: Insertar texto en un documento desde un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
