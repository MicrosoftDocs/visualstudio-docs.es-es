---
title: "Informaci&#243;n general sobre paneles de acciones"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "paneles de acciones [desarrollo de Office en Visual Studio]"
  - "paneles de acciones [desarrollo de Office en Visual Studio], acerca de los paneles de acciones"
  - "documentos inteligentes [desarrollo de Office en Visual Studio]"
  - "controles de usuario [desarrollo de Office en Visual Studio], paneles de acciones"
ms.assetid: 1b9b7db5-b19f-44ea-a774-f0962ca03bd2
caps.latest.revision: 101
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 100
---
# Informaci&#243;n general sobre paneles de acciones
  Un panel de acciones es un panel de tareas **Acciones de documentos** que se asocia a un documento específico de Microsoft Office Word o a un libro de Microsoft Office Excel.  Se aloja dentro del panel de tareas de Office junto con otros paneles de tareas integrados, como el panel de tareas **Origen XML** de Excel o el panel de tareas **Estilos y formato** de Word.  Puede utilizar controles de Windows Forms o WPF para diseñar la interfaz de usuario del panel de acciones.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Puede crear un panel de acciones solo en una personalización de nivel de documento para Word o Excel.  No se puede crear un panel de acciones en un complemento de VSTO.  Para obtener más información, consulte [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  El panel de acciones difiere de los paneles de tareas personalizados.  Los paneles de tareas personalizados están asociados a la aplicación, no a un documento específico.  Puede crear paneles de tareas personalizados en complementos de VSTO para algunas aplicaciones de Microsoft Office.  Para obtener más información, vea [Paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Para ver una demostración en vídeo relacionada, consulte [Cómo: Usar controles WPF dentro de un panel de acciones de Excel](http://go.microsoft.com/fwlink/?LinkId=132763).  
  
## Mostrar el panel de acciones  
 El panel de acciones se representa mediante la clase <xref:Microsoft.Office.Tools.ActionsPane>.  Cuando crea un proyecto de nivel de documento, una instancia de esta clase está disponible para el código mediante el uso del campo `ActionsPane` de la clase `ThisWorkbook` \(para Excel\) o `ThisDocument` \(para Word\) en el proyecto.  Para mostrar el panel de acciones, agregue un control de Windows Forms a la propiedad <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> del campo `ActionsPane`.  En el siguiente ejemplo de código se agrega un control denominado `actions` al panel de acciones.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#7)]
 [!code-vb[Trin_VstcoreActionsPaneWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#7)]  
  
 El panel de acciones se vuelve visible en tiempo de ejecución desde el momento que usted le agrega un control de forma explícita.  Una vez que se muestre el panel de acciones, puede agregar o quitar controles de forma dinámica en respuesta a las acciones del usuario.  Normalmente debe agregar el código para mostrar el panel de acciones en el controlador de eventos `Startup` de `ThisDocument` o `ThisWorkbook` para que el panel de acciones esté visible cuando el usuario abra el documento por primera vez.  Sin embargo, puede que le interese mostrar el panel de acciones solo como respuesta a una acción del usuario en el documento.  Por ejemplo, podría agregar código para el evento `Click` de un control en el documento.  
  
### Agregar varios controles al panel de acciones  
 Si va a agregar varios controles al panel de acciones, en la mayoría de los casos debería agrupar los controles en un control de usuario y, a continuación, agregar el control de usuario a la propiedad <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>.  Este proceso incluye los siguientes pasos:  
  
1.  Crear la interfaz de usuario \(UI\) del panel de acciones agregando un elemento de **Control del panel de acciones** o de **Control de usuario** a su proyecto.  Ambos elementos incluyen una clase <xref:System.Windows.Forms.UserControl> de Windows Forms personalizada.  Los elementos **Control del panel de acciones** y **Control de usuario** son equivalentes; solo se diferencian en su nombre.  
  
2.  Agregue controles de Windows Forms al <xref:System.Windows.Forms.UserControl> mediante el diseñador o escribiendo código.  
  
    > [!NOTE]  
    >  También puede agregar controles WPF al panel de acciones agregando un WPF <xref:System.Windows.Controls.UserControl> al <xref:System.Windows.Forms.UserControl> de Windows Forms.  Para obtener más información, vea [Usar controles de WPF en soluciones de Office](../vsto/using-wpf-controls-in-office-solutions.md).  
  
3.  Agregue una instancia del control de usuario personalizado a los controles contenidos en el campo `ActionsPane` de la clase `ThisWorkbook` \(para Excel\) o `ThisDocument` \(para Word\) en el proyecto.  
  
 Para obtener ejemplos que demuestren este proceso más detalladamente, consulte este artículo que explica [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
## Ocultar el panel de acciones  
 Aunque la clase <xref:Microsoft.Office.Tools.ActionsPane> tiene un método <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> y una propiedad <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A>, no puede quitar el panel de acciones de la interfaz de usuario utilizando ningún miembro de la propia clase <xref:Microsoft.Office.Tools.ActionsPane>.  Llamar al método <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> o establecer la propiedad <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> en **false** solo oculta los controles en el panel de acciones, no el panel de tareas.  
  
 Para ocultar el panel de tareas en la solución, tiene varias opciones:  
  
-   Para Word, establezca en **false** la propiedad <xref:Microsoft.Office.Interop.Word.TaskPane.Visible%2A> del objeto <xref:Microsoft.Office.Interop.Word.TaskPane> que representa el panel de tareas Acciones de documentos.  El siguiente ejemplo de código está diseñado para ejecutarse desde la clase `ThisDocument` del proyecto.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#34](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreActionsPaneWord#34](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#34)]  
  
-   Para Excel, establezca la propiedad <xref:Microsoft.Office.Interop.Excel._Application.DisplayDocumentActionTaskPane%2A> del objeto <xref:Microsoft.Office.Tools.Excel.Workbook.Application%2A> en **false**.  El siguiente ejemplo de código está diseñado para ejecutarse desde la clase `ThisWorkbook` del proyecto.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#11)]  
  
-   Para Word o Excel, también puede establecer la propiedad <xref:Microsoft.Office.Core.CommandBar.Visible%2A> de la barra de comandos que representa el panel de tareas en **false**.  El siguiente ejemplo de código está diseñado para ejecutarse desde la clase `ThisDocument` o `ThisWorkbook` del proyecto.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#9)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#9)]  
  
### Borrar el panel de acciones cuando se abre el documento  
 Si el usuario guarda el documento mientras está visible el panel de acciones, el panel de acciones estará visible cada vez que se abra el documento, independientemente de que el panel de acciones contenga o no algún control.  Si desea controlar cuando se muestra, llame al método <xref:Microsoft.Office.Tools.ActionsPane.Clear%2A> del campo `ActionsPane` en el controlador de eventos `Startup` de `ThisDocument` o `ThisWorkbook` para asegurarse de que el panel de acciones no esté visible cuando se abra el documento.  
  
### Determinar cuándo se cierra el panel de acciones  
 No se genera ningún evento cuando se cierra el panel de acciones.  Aunque la clase <xref:Microsoft.Office.Tools.ActionsPane> tiene un evento <xref:Microsoft.Office.Tools.ActionsPane.VisibleChanged>, este evento no se genera cuando el usuario final cierra el panel de acciones.  En su lugar, este evento se genera cuando se ocultan los controles del panel de acciones llamando al método <xref:Microsoft.Office.Tools.ActionsPane.Hide%2A> o estableciendo la propiedad <xref:Microsoft.Office.Tools.ActionsPane.Visible%2A> en **false**.  
  
 Si el usuario final cierra el panel de acciones, el usuario puede lograr que se vuelva a mostrar llevando a cabo uno de los siguientes procedimientos en la interfaz de usuario \(UI\) de la aplicación.  
  
##### Para mostrar el panel de acciones mediante la interfaz de usuario de Word o Excel  
  
1.  Haga clic en la pestaña **Ver** de la cinta.  
  
2.  En el grupo **Mostrar u ocultar**, haga clic en el botón de alternancia **Acciones de documentos**.  
  
## Programar eventos del panel de acciones  
 Puede agregar varios controles de usuario al panel de acciones y, a continuación, escribir código para responder a eventos en el documento mostrando y ocultando los controles de usuario.  Si asigna elementos de esquema XML a su documento, puede mostrar determinados controles de usuario en el panel de acciones siempre que el punto de inserción esté dentro de uno de los elementos XML.  Para obtener más información, consulte los siguientes artículos, que explican [Cómo: Asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md) y [Cómo: Asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md).  
  
 También puede escribir código para responder a los eventos de cualquier objeto, incluyendo eventos de control host, aplicación o documento.  Para obtener más información, consulte [Tutorial: Programar basándose en los eventos de un control NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
## Enlazar datos a controles en el panel de acciones  
 Los controles del panel de acciones tienen las mismas capacidades de enlace de datos que los controles de Windows Forms.  Puede enlazar los controles a orígenes de datos, como conjuntos de datos, conjuntos de datos con tipo y XML.  Para obtener más información, consulte [Enlace de datos y formularios Windows Forms](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27).  
  
 Puede enlazar controles en el panel de acciones y controles en el documento al mismo conjunto de datos.  Por ejemplo, puede crear una relación maestro y detalles entre los controles del panel de acciones y los controles de la hoja de cálculo.  Para obtener más información, consulte [Tutorial: Enlazar datos a controles en un panel de acciones de Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
## Validar datos en los controles del panel de acciones  
 Si se muestra un cuadro de mensaje en el controlador de eventos <xref:System.Windows.Forms.Control.Validating> de un control en el panel de acciones, el evento podría generarse una segunda vez al pasar el foco del control al cuadro de mensaje.  Para evitar este problema, utilice un control <xref:System.Windows.Forms.ErrorProvider> para mostrar cualquier mensaje de error de validación.  
  
## Orden de apilamiento de controles de usuario  
 Si está utilizando varios controles de usuario, puede escribir código para apilar correctamente los controles de usuario en el panel de acciones, independientemente de que esté acoplado vertical u horizontalmente.  Puede establecer el orden de apilamiento de los controles de usuario en el panel de acciones mediante la enumeración <xref:Microsoft.Office.Tools.StackStyle> de la propiedad <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A>.  Para obtener más información, consulte [Cómo: Administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md).  
  
 La propiedad <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> puede tomar los siguientes <xref:Microsoft.Office.Tools.StackStyle> valores de enumeración.  
  
|Estilo de apilamiento|Definición|  
|---------------------------|----------------|  
|FromBottom|Apilar desde la parte inferior del panel de acciones.|  
|FromLeft|Apilar desde la parte izquierda del panel de acciones.|  
|FromRight|Apilar desde la parte derecha del panel de acciones.|  
|FromTop|Apilar desde la parte superior del panel de acciones.|  
|None|Sin orden de apilamiento definido; el desarrollador controla el orden.|  
  
 El código siguiente establece la propiedad <xref:Microsoft.Office.Tools.ActionsPane.StackOrder%2A> para que apile los controles de usuario desde la parte superior del panel de acciones.  
  
 [!code-csharp[Trin_VstcoreActionsPaneExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#10)]
 [!code-vb[Trin_VstcoreActionsPaneExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#10)]  
  
## Anclar controles  
 Si el usuario cambia el tamaño del panel de acciones en tiempo de ejecución, el tamaño de los controles podría cambiar junto con el panel de acciones.  Puede utilizar la propiedad <xref:System.Windows.Forms.Control.Anchor%2A> de un control de Windows Forms para anclar los controles al panel de acciones.  También puede anclar de la misma manera los controles de Windows Forms al control de usuario.  Para obtener más información, consulte [Cómo: Delimitar controles en formularios Windows Forms](http://msdn.microsoft.com/library/59ea914f-fbd3-427a-80fe-decd02f7ae6d).  
  
## Cambiar el tamaño del panel de acciones  
 No puede cambiar directamente el tamaño de un <xref:Microsoft.Office.Tools.ActionsPane> porque <xref:Microsoft.Office.Tools.ActionsPane> está incrustado en el panel de tareas.  Sin embargo, puede cambiar el ancho del panel de tareas mediante programación estableciendo la propiedad <xref:Microsoft.Office.Core.CommandBar.Width%2A> de la <xref:Microsoft.Office.Core.CommandBar> que representa el panel de tareas.  Puede cambiar la altura del panel de tareas si está acoplado horizontalmente o si está flotando.  
  
 Por lo general, no se recomienda cambiar mediante programación el tamaño del panel de tareas porque el usuario debería poder seleccionar el tamaño del panel de tareas que mejor se adapte a sus necesidades.  Sin embargo, si tiene que cambiar el ancho del panel de tareas, podría utilizar el siguiente código para hacerlo.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#102](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#102)]
 [!code-vb[Trin_VstcoreActionsPaneWord#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#102)]  
  
## Cambiar de posición el panel de acciones  
 No puede cambiar directamente la posición del <xref:Microsoft.Office.Tools.ActionsPane> porque está incrustado en el panel de tareas.  Sin embargo, puede mover el panel de tareas mediante programación estableciendo la propiedad <xref:Microsoft.Office.Core.CommandBar.Position%2A> de la <xref:Microsoft.Office.Core.CommandBar> que representa el panel de tareas.  
  
 Por lo general, no se recomienda cambiar la posición del panel de tareas mediante programación porque el usuario debería poder elegir la posición del panel de tareas que mejor se adapte a sus necesidades.  Sin embargo, si tiene que mover el panel de tareas hasta una posición concreta, podría utilizar el siguiente código para hacerlo.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#100](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreActionsPaneWord#100](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#100)]  
  
> [!NOTE]  
>  Los usuarios finales pueden cambiar manualmente la posición del panel de tareas en cualquier momento.  No hay ninguna manera de garantizar que el panel de tareas permanezca acoplado en la posición que indique mediante programación.  Sin embargo, puede comprobar los cambios de orientación y asegurarse de que los controles del panel de acciones se apilen en la dirección correcta.  Para obtener más información, consulte [Cómo: Administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md).  
  
 Establecer las propiedades <xref:Microsoft.Office.Tools.ActionsPane.Top%2A> y <xref:Microsoft.Office.Tools.ActionsPane.Left%2A> de <xref:Microsoft.Office.Tools.ActionsPane> no cambia su posición porque el objeto <xref:Microsoft.Office.Tools.ActionsPane> está incrustado en el panel de tareas.  
  
 Si el panel de tareas no está acoplado, puede establecer las propiedades <xref:Microsoft.Office.Core.CommandBar.Top%2A> y <xref:Microsoft.Office.Core.CommandBar.Left%2A> de <xref:Microsoft.Office.Core.CommandBar> que representa el panel de tareas.  El siguiente código mueve un panel de tareas desacoplado a la esquina superior izquierda del documento.  
  
 [!code-csharp[Trin_VstcoreActionsPaneWord#101](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#101)]
 [!code-vb[Trin_VstcoreActionsPaneWord#101](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#101)]  
  
## Vea también  
 [Usar controles de WPF en soluciones de Office](../vsto/using-wpf-controls-in-office-solutions.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Tutorial: Insertar texto en un documento de un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)   
 [Tutorial: Enlazar datos a controles en un panel de acciones de Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)   
 [Tutorial: Enlazar datos a controles en un panel de acciones de Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)   
 [Cómo: Administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Tutorial: Insertar texto en un documento de un panel de acciones](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md)  
  
  