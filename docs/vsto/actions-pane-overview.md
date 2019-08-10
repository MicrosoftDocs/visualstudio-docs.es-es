---
title: Información general del panel de acciones
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes [Office development in Visual Studio], about actions panes
- actions panes [Office development in Visual Studio]
- smart documents [Office development in Visual Studio]
- user controls [Office development in Visual Studio], actions panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6cbade56f80d75e6ab8d735aaf586d45d2dedb42
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926681"
---
# <a name="actions-pane-overview"></a>Información general del panel de acciones
  Un panel de acciones es un panel de tareas **acciones de documentos** personalizables que se adjunta a un determinado documento de Microsoft Office Word o Microsoft Office libro de Excel. El panel acciones se hospeda dentro del panel de tareas de Office junto con otros paneles de tareas integrados, como el panel de tareas **origen XML** en Excel o el panel de tareas **estilos y formato** de Word. Puede utilizar controles de Windows Forms o WPF para diseñar la interfaz de usuario del panel de acciones.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Puede crear un panel de acciones solo en una personalización de nivel de documento para Word o Excel. No se puede crear un panel de acciones en un complemento de VSTO. Para obtener más información, consulte [características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> El panel de acciones difiere de los paneles de tareas personalizados. Los paneles de tareas personalizados están asociados a la aplicación, no a un documento específico. Puede crear paneles de tareas personalizados en complementos de VSTO para algunas aplicaciones de Microsoft Office. Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).

 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") Para ver una demostración en vídeo relacionada, vea [cómo: ¿Usar controles de WPF dentro de un panel de acciones de Excel? ](http://go.microsoft.com/fwlink/?LinkId=132763).

## <a name="display-the-actions-pane"></a>Mostrar el panel de acciones
 El panel de acciones se representa mediante la clase <xref:Microsoft.Office.Tools.ActionsPane>. Cuando crea un proyecto de nivel de documento, una instancia de esta clase está disponible para el código mediante el uso del campo `ActionsPane` de la clase `ThisWorkbook` (para Excel) o `ThisDocument` (para Word) en el proyecto. Para mostrar el panel de acciones, agregue un control de Windows Forms a la propiedad <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> del campo `ActionsPane`. En el siguiente ejemplo de código se agrega un control denominado `actions` al panel de acciones.

 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

 El panel de acciones se vuelve visible en tiempo de ejecución en cuanto se agrega explícitamente un control. Una vez que se muestre el panel de acciones, puede agregar o quitar controles de forma dinámica en respuesta a las acciones del usuario. Normalmente debe agregar el código para mostrar el panel de acciones en el controlador de eventos `Startup` de `ThisDocument` o `ThisWorkbook` para que el panel de acciones esté visible cuando el usuario abra el documento por primera vez. Sin embargo, puede que le interese mostrar el panel de acciones solo como respuesta a una acción del usuario en el documento. Por ejemplo, podría agregar código para el evento `Click` de un control en el documento.

### <a name="add-multiple-controls-to-the-actions-pane"></a>Agregar varios controles al panel de acciones
 Al agregar varios controles al panel de acciones, debe agrupar los controles en un control de usuario y, a continuación, agregar el control <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> de usuario a la propiedad. Este proceso incluye los siguientes pasos:

1. Cree la interfaz de usuario (UI) del panel de acciones agregando un **control del panel de acciones** o un elemento de control de **usuario** al proyecto. Ambos elementos incluyen una clase <xref:System.Windows.Forms.UserControl> de Windows Forms personalizada. El **control del panel de acciones** y los elementos de **control de usuario** son equivalentes; la única diferencia es su nombre.

2. Agregue controles de Windows Forms al <xref:System.Windows.Forms.UserControl> mediante el diseñador o escribiendo código.

   > [!NOTE]
   > También puede agregar controles WPF al panel de acciones agregando un WPF <xref:System.Windows.Controls.UserControl> al <xref:System.Windows.Forms.UserControl> de Windows Forms. Para obtener más información, vea [usar controles de WPF en soluciones de Office](../vsto/using-wpf-controls-in-office-solutions.md).

3. Agregue una instancia del control de usuario personalizado a los controles contenidos en el campo `ActionsPane` de la clase `ThisWorkbook` (para Excel) o `ThisDocument` (para Word) en el proyecto.

   Para obtener ejemplos que muestran este proceso con más detalle, [consulte Cómo: Agregar un panel de acciones a documentos de Word o libros](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)de Excel.

## <a name="hide-the-actions-pane"></a>Ocultar el panel de acciones
 Aunque la clase <xref:Microsoft.Office.Tools.ActionsPane> tiene un método <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> y una propiedad <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>, no puede quitar el panel de acciones de la interfaz de usuario utilizando ningún miembro de la propia clase <xref:Microsoft.Office.Tools.ActionsPane>. Llamar al <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> método o establecer la <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> propiedad en **false** solo oculta los controles del panel de acciones; no oculta el panel de tareas.

 Para ocultar el panel de tareas en la solución, tiene varias opciones:

- En Word, establezca la <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> propiedad <xref:Microsoft.Office.Interop.Word.TaskPane> del objeto que representa el panel de tareas acciones de documento en **false**. El siguiente ejemplo de código está diseñado para ejecutarse desde la clase `ThisDocument` del proyecto.

     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#34)]

- En Excel, establezca la <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> propiedad <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> del objeto en **false**. El siguiente ejemplo de código está diseñado para ejecutarse desde la clase `ThisWorkbook` del proyecto.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#11)]

- En Word o Excel, también puede establecer la <xref:Microsoft.Office.Core.CommandBar.Visible%2A> propiedad de la barra de comandos que representa el panel de tareas en **false**. El siguiente ejemplo de código está diseñado para ejecutarse desde la clase `ThisDocument` o `ThisWorkbook` del proyecto.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#9)]

### <a name="clear-the-actions-pane-when-the-document-is-opened"></a>Borrar el panel de acciones cuando se abre el documento
 Cuando un usuario guarda el documento mientras el panel de acciones está visible, el panel de acciones está visible cada vez que se abre el documento, tanto si el panel de acciones contiene como si no. Si desea controlar cuando se muestra, llame al método <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> del campo `ActionsPane` en el controlador de eventos `Startup` de `ThisDocument` o `ThisWorkbook` para asegurarse de que el panel de acciones no esté visible cuando se abra el documento.

### <a name="determine-when-the-actions-pane-is-closed"></a>Determinar cuándo se cierra el panel de acciones
 No se genera ningún evento cuando se cierra el panel de acciones. Aunque la clase <xref:Microsoft.Office.Tools.ActionsPane> tiene un evento <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>, este evento no se genera cuando el usuario final cierra el panel de acciones. En su lugar, este evento se genera cuando se ocultan los controles del panel de acciones llamando <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> al método o estableciendo la <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> propiedad en **false**.

 Cuando el usuario cierra el panel de acciones, el usuario puede volver a mostrarlo mediante la ejecución de uno de los procedimientos siguientes en la interfaz de usuario (UI) de la aplicación.

##### <a name="to-display-the-actions-pane-by-using-the-ui-of-word-or-excel"></a>Para mostrar el panel de acciones mediante la interfaz de usuario de Word o Excel

1. En la cinta de opciones, haga clic en la pestaña **Ver** .

2. En el grupo **Mostrar u ocultar** , haga clic en el botón de alternancia **acciones de documento** .

## <a name="program-actions-pane-events"></a>Eventos del panel de acciones de programa
 Puede agregar varios controles de usuario al panel de acciones y, a continuación, escribir código para responder a eventos en el documento mostrando y ocultando los controles de usuario. Si asigna elementos de esquema XML a su documento, puede mostrar determinados controles de usuario en el panel de acciones siempre que el punto de inserción esté dentro de uno de los elementos XML. Para obtener más información, consulte [Cómo Asigne esquemas a documentos de Word dentro de](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) visual [Studio y cómo: Asignar esquemas a hojas de cálculo en Visual](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)Studio.

 También puede escribir código para responder a los eventos de cualquier objeto, incluyendo eventos de control host, aplicación o documento. Para obtener más información, vea [Tutorial: Programar contra eventos de un control](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)NamedRange.

## <a name="bind-data-to-controls-on-the-actions-pane"></a>Enlazar datos a controles en el panel de acciones
 Los controles del panel de acciones tienen las mismas capacidades de enlace de datos que los controles de Windows Forms. Puede enlazar los controles a orígenes de datos, como conjuntos de datos, conjuntos de datos con tipo y XML. Para obtener más información, consulte [enlace de datos y Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 Puede enlazar controles en el panel de acciones y controles en el documento al mismo conjunto de datos. Por ejemplo, puede crear una relación maestro y detalles entre los controles del panel de acciones y los controles de la hoja de cálculo. Para obtener más información, vea [Tutorial: Enlazar datos a controles en un panel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)de acciones de Excel.

## <a name="validate-data-in-actions-pane-controls"></a>Validar datos en los controles del panel de acciones
 Si se muestra un cuadro de mensaje en el controlador de eventos <xref:System.Windows.Forms.Control.Validating> de un control en el panel de acciones, el evento podría generarse una segunda vez al pasar el foco del control al cuadro de mensaje. Para evitar este problema, utilice un control <xref:System.Windows.Forms.ErrorProvider> para mostrar cualquier mensaje de error de validación.

## <a name="user-control-stacking-order"></a>Orden de apilamiento de controles de usuario
 Si está utilizando varios controles de usuario, puede escribir código para apilar correctamente los controles de usuario en el panel de acciones, independientemente de que esté acoplado vertical u horizontalmente. Puede establecer el orden de apilamiento de los controles de usuario en el panel de acciones mediante la enumeración <xref:Microsoft.Office.Tools.StackStyle> de la propiedad <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>. Para obtener más información, vea [Cómo: Administrar el diseño de controles en](../vsto/how-to-manage-control-layout-on-actions-panes.md)los paneles de acciones.

 La propiedad <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> puede tomar los siguientes <xref:Microsoft.Office.Tools.StackStyle> valores de enumeración.

|Estilo de apilamiento|Definición|
|--------------------|----------------|
|FromBottom|Apilar desde la parte inferior del panel de acciones.|
|FromLeft|Apilar desde la parte izquierda del panel de acciones.|
|FromRight|Apilar desde la parte derecha del panel de acciones.|
|FromTop|Apilar desde la parte superior del panel de acciones.|
|None|Sin orden de apilamiento definido; el desarrollador controla el orden.|

 El código siguiente establece la propiedad <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> para que apile los controles de usuario desde la parte superior del panel de acciones.

 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#10)]

## <a name="anchor-controls"></a>Delimitar controles
 Si el usuario cambia el tamaño del panel de acciones en tiempo de ejecución, los controles pueden cambiar de tamaño con el panel de acciones. Puede utilizar la propiedad <xref:System.Windows.Forms.Control.Anchor%2A> de un control de Windows Forms para anclar los controles al panel de acciones. También puede anclar de la misma manera los controles de Windows Forms al control de usuario. Para obtener más información, consulte [Cómo Delimite los](/dotnet/framework/winforms/controls/how-to-anchor-controls-on-windows-forms)controles en Windows Forms.

## <a name="resize-the-actions-pane"></a>Cambiar el tamaño del panel de acciones
 No puede cambiar directamente el tamaño de un <xref:Microsoft.Office.Tools.ActionsPane> porque <xref:Microsoft.Office.Tools.ActionsPane> está incrustado en el panel de tareas. Sin embargo, puede cambiar el ancho del panel de tareas mediante programación estableciendo la propiedad <xref:Microsoft.Office.Core.CommandBar.Width%2A> de la <xref:Microsoft.Office.Core.CommandBar> que representa el panel de tareas. Puede cambiar la altura del panel de tareas si está acoplado horizontalmente o si está flotando.

 No se recomienda cambiar el tamaño del panel de tareas mediante programación, ya que el usuario debe poder seleccionar el tamaño del panel de tareas que mejor se adapte a sus necesidades. Sin embargo, si tiene que cambiar el ancho del panel de tareas, podría utilizar el siguiente código para hacerlo.

 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#102)]

## <a name="reposition-the-actions-pane"></a>Cambiar la posición del panel de acciones
 No puede cambiar directamente la posición del <xref:Microsoft.Office.Tools.ActionsPane> porque está incrustado en el panel de tareas. Sin embargo, puede mover el panel de tareas mediante programación estableciendo la propiedad <xref:Microsoft.Office.Core.CommandBar.Position%2A> de la <xref:Microsoft.Office.Core.CommandBar> que representa el panel de tareas.

 No se recomienda cambiar la posición del panel de tareas mediante programación porque el usuario debería poder elegir la posición del panel de tareas en la pantalla que mejor se adapte a sus necesidades. Sin embargo, si tiene que mover el panel de tareas hasta una posición concreta, podría utilizar el siguiente código para hacerlo.

 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#100)]

> [!NOTE]
> Los usuarios finales pueden cambiar manualmente la posición del panel de tareas en cualquier momento. No hay ninguna manera de garantizar que el panel de tareas permanezca acoplado en la posición que indique mediante programación. Sin embargo, puede comprobar los cambios de orientación y asegurarse de que los controles del panel de acciones se apilen en la dirección correcta. Para obtener más información, consulte [Cómo Administrar el diseño de controles en](../vsto/how-to-manage-control-layout-on-actions-panes.md)los paneles de acciones.

 Establecer las <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> propiedades <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> y de <xref:Microsoft.Office.Tools.ActionsPane> no cambia su posición porque el <xref:Microsoft.Office.Tools.ActionsPane> objeto está incrustado en el panel de tareas.

 Si el panel de tareas no está acoplado, puede establecer las propiedades <xref:Microsoft.Office.Core.CommandBar.Top%2A> y <xref:Microsoft.Office.Core.CommandBar.Left%2A> de <xref:Microsoft.Office.Core.CommandBar> que representa el panel de tareas. El siguiente código mueve un panel de tareas desacoplado a la esquina superior izquierda del documento.

 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#101)]

## <a name="see-also"></a>Vea también
- [Usar controles de WPF en soluciones de Office](../vsto/using-wpf-controls-in-office-solutions.md)
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Procedimientos: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Tutorial: Insertar texto en un documento desde un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
- [Tutorial: Enlazar datos a controles en un panel de acciones de Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)
- [Tutorial: Enlazar datos a controles en un panel de acciones de Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)
- [Cómo: Administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Tutorial: Insertar texto en un documento desde un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)
