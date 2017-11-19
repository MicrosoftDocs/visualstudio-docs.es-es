---
title: 'Tutorial: Enlazar datos a controles en un panel de acciones de Word | Documentos de Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], data binding
- actions panes [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], smart documents
- data binding [Office development in Visual Studio], actions panes
- actions panes [Office development in Visual Studio], binding controls
- smart documents [Office development in Visual Studio], data binding
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: "64"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6a70bd325a5a9e20f9a67e59f81c63ce4b1ddcc4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-binding-data-to-controls-on-a-word-actions-pane"></a>Tutorial: Enlazar datos a controles en un panel de acciones de Word
  Este tutorial muestra el enlace de datos a controles en un panel de acciones de Word. Los controles muestran una relación principal-detalle entre las tablas de una base de datos de SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un panel de acciones con controles de formularios Windows Forms que están enlazados a datos.  
  
-   Uso de una relación principal-detalle para mostrar datos en los controles.  
  
-   Mostrar el panel de acciones cuando se abre la aplicación.  
  
> [!NOTE]  
>  Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Acceso a un servidor con la base de datos de ejemplo Northwind de SQL Server.  
  
-   Permisos para leer y escribir en la base de datos de SQL Server.  
  
## <a name="creating-the-project"></a>Crear el proyecto  
 El primer paso es crear un proyecto de tipo Documento de Word.  
  
#### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Cree un proyecto de documento de Word con el nombre **Mi panel de acciones de Word**. En el asistente, seleccione **crear un nuevo documento**.  
  
     Para obtener más información, consulta [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el **Mi panel de acciones de Word** proyecto al **el Explorador de soluciones**.  
  
## <a name="adding-controls-to-the-actions-pane"></a>Agregar controles al panel de acciones  
 En este tutorial, necesita un control de panel de acciones que contiene controles de formularios Windows Forms enlazados a datos. Agregar un origen de datos al proyecto y, a continuación, arrastre controles desde el **orígenes de datos** ventana para el control de panel de acciones.  
  
#### <a name="to-add-an-actions-pane-control"></a>Para agregar un control de panel de acciones  
  
1.  Seleccione el **Mi panel de acciones de Word** proyecto **el Explorador de soluciones**.  
  
2.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
3.  En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **Control del panel de acciones**, asígnele el nombre **ActionsControl**y, a continuación, haga clic en **agregar**.  
  
#### <a name="to-add-a-data-source-to-the-project"></a>Para agregar un origen de datos al proyecto  
  
1.  Si la ventana **Orígenes de datos** no es visible, muéstrela; para ello, en la barra de menús, elija **Ver**, **Otras ventanas**, **Orígenes de datos**.  
  
    > [!NOTE]  
    >  Si **Mostrar orígenes de datos** no está disponible, haga clic en el documento de Word y, a continuación, compruebe de nuevo.  
  
2.  Haga clic en **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Seleccione **base de datos** y, a continuación, haga clic en **siguiente**.  
  
4.  Seleccione una conexión de datos a la base de datos de SQL Server de ejemplo Northwind, o agregar una nueva conexión mediante el **nueva conexión** botón.  
  
5.  Haga clic en **Siguiente**.  
  
6.  Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic en **siguiente**.  
  
7.  Expanda el **tablas** nodo en el **objetos de base de datos** ventana.  
  
8.  Active la casilla situada junto a la **proveedores** y **productos** tablas.  
  
9. Haga clic en **Finalizar**.  
  
 El asistente agrega la **proveedores** tabla y **productos** la tabla a la **orígenes de datos** ventana. También agrega un conjunto de datos con tipo al proyecto que está visible en **el Explorador de soluciones**.  
  
#### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Para agregar controles de formularios Windows Forms enlazados a datos a un control de panel de acciones  
  
1.  En el **orígenes de datos** ventana, expanda la **proveedores** tabla.  
  
2.  Haga clic en la flecha de lista desplegable en el **nombre de la compañía** nodo y seleccione **ComboBox**.  
  
3.  Arrastre **CompanyName** desde el **orígenes de datos** ventana para el control de panel de acciones.  
  
     Un <xref:System.Windows.Forms.ComboBox> control se crea en el control de panel de acciones. Al mismo tiempo, un <xref:System.Windows.Forms.BindingSource> denominado `SuppliersBindingSource`, un adaptador de tabla y un <xref:System.Data.DataSet> se agregan al proyecto en la Bandeja de componentes.  
  
4.  Seleccione `SuppliersBindingNavigator` en el **componente** bandeja del sistema y presione SUPR. No usará el `SuppliersBindingNavigator` en este tutorial.  
  
    > [!NOTE]  
    >  Eliminar el `SuppliersBindingNavigator` no se quita todo el código generado para él. Puede quitar este código.  
  
5.  Mueva el cuadro combinado para que se encuentre bajo la etiqueta y cambie la **tamaño** propiedad **171, 21**.  
  
6.  En el **orígenes de datos** ventana, expanda la **productos** tabla que es un elemento secundario de la **proveedores** tabla.  
  
7.  Haga clic en la flecha de lista desplegable en el **ProductName** nodo y seleccione **ListBox**.  
  
8.  Arrastre **ProductName** al control del panel de acciones.  
  
     Un <xref:System.Windows.Forms.ListBox> control se crea en el control de panel de acciones. Al mismo tiempo, un <xref:System.Windows.Forms.BindingSource> denominado `ProductBindingSource` y un adaptador de tabla se agregan al proyecto en la Bandeja de componentes.  
  
9. Mover el cuadro de lista, por lo que se encuentre bajo la etiqueta y cambie la **tamaño** propiedad **171,95**.  
  
10. Arrastre un <xref:System.Windows.Forms.Button> desde el **cuadro de herramientas** en el panel de acciones de control y colóquelo debajo del cuadro de lista.  
  
11. Haga clic en el <xref:System.Windows.Forms.Button>, haga clic en **propiedades** en el menú contextual y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |--------------|-----------|  
    |**Nombre**|**Insertar**|  
    |**Texto**|**Insertar**|  
  
12. Cambiar el tamaño del control de usuario para ajustar los controles.  
  
## <a name="setting-up-the-data-source"></a>Cómo configurar el origen de datos  
 Para configurar el origen de datos, agregue código a la <xref:System.Windows.Forms.UserControl.Load> eventos del control del panel de acciones para rellenar el control con los datos de la <xref:System.Data.DataTable>y establezca el <xref:System.Windows.Forms.Binding.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A> propiedades para cada control.  
  
#### <a name="to-load-the-control-with-data"></a>Para cargar el control con datos  
  
1.  En el <xref:System.Windows.Forms.UserControl.Load> controlador de eventos de la `ActionsControl` de clases, agregue el código siguiente.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]  
  
2.  En C#, debe asociar el controlador de eventos para el <xref:System.Windows.Forms.UserControl.Load> eventos. Puede colocar este código en el `ActionsControl` constructor después de llamar a `InitializeComponent`. Para obtener más información sobre cómo crear controladores de eventos, vea [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]  
  
#### <a name="to-set-data-binding-properties-of-the-controls"></a>Para establecer las propiedades de enlace de datos de los controles  
  
1.  Seleccione el control `CompanyNameComboBox`.  
  
2.  En el **propiedades** ventana, haga clic en el botón a la derecha de la **DataSource** propiedad y seleccione **suppliersBindingSource**.  
  
3.  Haga clic en el botón a la derecha de la **DisplayMember** propiedad y seleccione **CompanyName**.  
  
4.  Expanda el **DataBindings** propiedad, haga clic en el botón a la derecha de la **texto** propiedad y seleccione **ninguno**.  
  
5.  Seleccione el control `ProductNameListBox`.  
  
6.  En el **propiedades** ventana, haga clic en el botón a la derecha de la **DataSource** propiedad y seleccione **productsBindingSource**.  
  
7.  Haga clic en el botón a la derecha de la **DisplayMember** propiedad y seleccione **ProductName**.  
  
8.  Expanda el **DataBindings** propiedad, haga clic en el botón a la derecha de la **SelectedValue** propiedad y seleccione **ninguno**.  
  
## <a name="adding-a-method-to-insert-data-into-a-table"></a>Agregar un método para insertar datos en una tabla  
 La siguiente tarea consiste en leer los datos de los controles enlazados y rellenar una tabla en el documento de Word. En primer lugar, cree un procedimiento para dar formato a los encabezados de la tabla y, a continuación, agregue el `AddData` método para crear y dar formato a una tabla de Word.  
  
#### <a name="to-format-the-table-headings"></a>Para dar formato a los encabezados de tabla  
  
1.  En la `ActionsControl` de clases, cree un método para dar formato a los encabezados de la tabla.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]  
  
#### <a name="to-create-the-table"></a>Para crear la tabla  
  
1.  En la `ActionsControl` de clases, escribir un método que va a crear una tabla si todavía no existe ninguno y agregar datos desde el panel de acciones a la tabla.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]  
  
#### <a name="to-insert-text-into-a-word-table"></a>Para insertar texto en una tabla de Word  
  
1.  Agregue el código siguiente a la <xref:System.Windows.Forms.Control.Click> controlador de eventos de la **insertar** botón.  
  
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]  
  
2.  En C#, debe crear un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> eventos del botón.  Puede colocar este código en el <xref:System.Windows.Forms.UserControl.Load> controlador de eventos de la `ActionsControl` clase.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]  
  
## <a name="showing-the-actions-pane"></a>Mostrar el panel de acciones  
 El panel de acciones se vuelve visible después de que se agregan a él.  
  
#### <a name="to-show-the-actions-pane"></a>Para mostrar el panel de acciones  
  
1.  En **el Explorador de soluciones**, haga clic en **ThisDocument.vb** o **ThisDocument.cs**y, a continuación, haga clic en **ver código** en el menú contextual.  
  
2.  Crear una nueva instancia del control en la parte superior de la `ThisDocument` clase para que tenga un aspecto similar al ejemplo siguiente.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]  
  
3.  Agregue código a la <xref:Microsoft.Office.Tools.Word.Document.Startup> controlador de eventos de `ThisDocument` para que tenga un aspecto similar al ejemplo siguiente.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]  
  
## <a name="testing-the-application"></a>Probar la aplicación  
 Ahora puede probar el documento para comprobar que el panel de acciones aparece cuando se abre el documento. Probar la relación maestro y detalles en los controles del panel de acciones y asegúrese de que se rellenan los datos en una palabra tabla cuando la **insertar** se hace clic en el botón.  
  
#### <a name="to-test-your-document"></a>Para probar el documento  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Confirme que el panel de acciones esté visible.  
  
3.  Seleccione una empresa en el cuadro combinado y compruebe que los elementos de la **productos** cambio de cuadro de lista.  
  
4.  Seleccionar un producto, haga clic en **insertar** en el panel Acciones y compruebe que los detalles del producto se agregan a la tabla de Word.  
  
5.  Inserte otros productos de diferentes empresas.  
  
## <a name="next-steps"></a>Pasos siguientes  
 En este tutorial se muestra los aspectos básicos de enlazar datos a controles en un panel de acciones de Word. A continuación, podría realizar las siguientes tareas:  
  
-   Enlazar datos a controles en Excel. Para obtener más información, consulte [Tutorial: enlazar datos a controles en un panel de acciones de Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Implementar el proyecto. Para obtener más información, consulte [implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Enlace de datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  