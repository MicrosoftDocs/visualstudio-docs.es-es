---
title: 'Tutorial: enlazar datos a controles en un panel de acciones de Word'
description: Enlazar datos a controles en un panel de acciones de Microsoft Word. Los controles muestran una relación principal-detalle entre las tablas de una base de datos de SQL Server.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7599348b0c44b7239305bb5af49ee2f5c51d882b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906583"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Tutorial: enlazar datos a controles en un panel de acciones de Word
  En este tutorial se muestra cómo enlazar datos a controles en un panel de acciones de Word. Los controles muestran una relación principal-detalle entre las tablas de una base de datos de SQL Server.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Crear un panel de acciones con Windows Forms controles que están enlazados a datos.

- Usar una relación principal-detalle para mostrar los datos de los controles.

- Mostrar el panel de acciones cuando se abra la aplicación.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Acceso a un servidor con la base de datos de ejemplo Northwind SQL Server.

- Permisos para leer y escribir en la base de datos de SQL Server.

## <a name="create-the-project"></a>Creación del proyecto
 El primer paso es crear un proyecto de tipo Documento de Word.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de documento de Word con el nombre **mi panel de acciones de Word**. En el asistente, seleccione **crear un nuevo documento**.

     Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el proyecto **Panel mis acciones de Word** a **Explorador de soluciones**.

## <a name="add-controls-to-the-actions-pane"></a>Agregar controles al panel de acciones
 En este tutorial, necesitará un control del panel de acciones que contenga controles de Windows Forms enlazados a datos. Agregue un origen de datos al proyecto y, a continuación, arrastre los controles desde la ventana **orígenes de datos** hasta el control panel de acciones.

### <a name="to-add-an-actions-pane-control"></a>Para agregar un control del panel de acciones

1. Seleccione el proyecto **mi panel de acciones de Word** en **Explorador de soluciones**.

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **control del panel de acciones**, asígnele el nombre **ActionsControl** y, a continuación, haga clic en **Agregar**.

### <a name="to-add-a-data-source-to-the-project"></a>Para agregar un origen de datos al proyecto

1. Si la ventana **orígenes de datos** no está visible, puede mostrarla en la barra de menús y elegir **Ver**  >  **otros**  >  **orígenes de datos** de Windows.

   > [!NOTE]
   > Si **Mostrar orígenes de datos** no está disponible, haga clic en el documento de Word y, a continuación, vuelva a comprobarlo.

2. Haga clic en **Agregar nuevo origen de datos** para iniciar el **Asistente para la configuración de orígenes de datos**.

3. Seleccione **base de datos** y, a continuación, haga clic en **siguiente**.

4. Seleccione una conexión de datos a la base de datos de ejemplo Northwind SQL Server o agregue una nueva conexión mediante el botón **nueva conexión** .

5. Haga clic en **Siguiente**.

6. Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic en **siguiente**.

7. Expanda el nodo **tablas** en la ventana **objetos de base de datos** .

8. Active la casilla situada junto a las tablas **proveedores** y **productos** .

9. Haga clic en **Finalizar**

   El asistente agrega la tabla **proveedores** y la tabla **productos** a la ventana **orígenes de datos** . También agrega un conjunto de un objeto con tipo al proyecto que está visible en **Explorador de soluciones**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Para agregar controles de Windows Forms enlazados a datos a un control del panel de acciones

1. En la ventana **orígenes de datos** , expanda la tabla **proveedores** .

2. Haga clic en la flecha desplegable del nodo nombre de la **compañía** y seleccione **ComboBox**.

3. Arrastre **CompanyName** desde la ventana **orígenes de datos** hasta el control panel de acciones.

     <xref:System.Windows.Forms.ComboBox>Se crea un control en el control del panel de acciones. Al mismo tiempo, <xref:System.Windows.Forms.BindingSource> `SuppliersBindingSource` se agregan al proyecto un nombre, un adaptador de tabla y un <xref:System.Data.DataSet> elemento en la bandeja de componentes.

4. Seleccione `SuppliersBindingNavigator` en la bandeja de **componentes** y presione **Supr**. No usará `SuppliersBindingNavigator` en este tutorial.

    > [!NOTE]
    > Al eliminar el no se `SuppliersBindingNavigator` quita todo el código que se generó para él. Puede quitar este código.

5. Mueva el cuadro combinado para que esté bajo la etiqueta y cambie la propiedad **size** a **171, 21**.

6. En la ventana **orígenes de datos** , expanda la tabla **Products** que sea un elemento secundario de la tabla **Suppliers** .

7. Haga clic en la flecha desplegable del nodo **NombreProducto** y seleccione **ListBox**.

8. Arrastre **ProductName** al control panel de acciones.

     <xref:System.Windows.Forms.ListBox>Se crea un control en el control del panel de acciones. Al mismo tiempo, <xref:System.Windows.Forms.BindingSource> `ProductBindingSource` se agregan al proyecto un nombre y un adaptador de tabla en la bandeja de componentes.

9. Mueva el cuadro de lista para que esté debajo de la etiqueta y cambie la propiedad **size** a **171, 95**.

10. Arrastre un <xref:System.Windows.Forms.Button> desde el cuadro de **herramientas** hasta el control del panel de acciones y colóquelo debajo del cuadro de lista.

11. Haga clic con el botón secundario en el <xref:System.Windows.Forms.Button> , haga clic en **propiedades** en el menú contextual y cambie las propiedades siguientes.

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**Insertar**|
    |**Texto**|**Insertar**|

12. Cambie el tamaño del control de usuario para que se ajuste a los controles.

## <a name="set-up-the-data-source"></a>Configuración del origen de datos
 Para configurar el origen de datos, agregue código al <xref:System.Windows.Forms.UserControl.Load> evento del control del panel de acciones para rellenar el control con los datos de y <xref:System.Data.DataTable> establecer <xref:System.Windows.Forms.Binding.DataSource%2A> las <xref:System.Windows.Forms.BindingSource.DataMember%2A> propiedades y de cada control.

### <a name="to-load-the-control-with-data"></a>Para cargar el control con datos

1. En el <xref:System.Windows.Forms.UserControl.Load> controlador de eventos de la `ActionsControl` clase, agregue el código siguiente.

     [!code-vb[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#1)]

2. En C#, debe asociar el controlador de eventos al <xref:System.Windows.Forms.UserControl.Load> evento. Puede colocar este código en el `ActionsControl` constructor, después de la llamada a `InitializeComponent` . Para obtener más información sobre cómo crear controladores de eventos, consulte [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#33)]

### <a name="to-set-data-binding-properties-of-the-controls"></a>Para establecer las propiedades de enlace de datos de los controles

1. Seleccione el control `CompanyNameComboBox`.

2. En la ventana **propiedades** , haga clic en el botón situado a la derecha de la propiedad **DataSource** y seleccione **suppliersBindingSource**.

3. Haga clic en el botón situado a la derecha de la propiedad **DisplayMember** y seleccione **CompanyName**.

4. Expanda la propiedad **DataBindings** , haga clic en el botón situado a la derecha de la propiedad **Text** y seleccione **ninguno**.

5. Seleccione el control `ProductNameListBox`.

6. En la ventana **propiedades** , haga clic en el botón situado a la derecha de la propiedad **DataSource** y seleccione **productsBindingSource**.

7. Haga clic en el botón situado a la derecha de la propiedad **DisplayMember** y seleccione **ProductName**.

8. Expanda la propiedad **DataBindings** , haga clic en el botón situado a la derecha de la propiedad **SelectedValue** y seleccione **ninguno**.

## <a name="add-a-method-to-insert-data-into-a-table"></a>Agregar un método para insertar datos en una tabla
 La siguiente tarea consiste en leer los datos de los controles enlazados y rellenar una tabla en el documento de Word. En primer lugar, cree un procedimiento para dar formato a los encabezados de la tabla y, a continuación, agregue el `AddData` método para crear y dar formato a una tabla de Word.

### <a name="to-format-the-table-headings"></a>Para dar formato a los encabezados de tabla

1. En la `ActionsControl` clase, cree un método para dar formato a los encabezados de la tabla.

     [!code-vb[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#2)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#2)]

### <a name="to-create-the-table"></a>Para crear la tabla

1. En la `ActionsControl` clase, escriba un método que cree una tabla si aún no existe ninguna y agregue los datos del panel de acciones a la tabla.

     [!code-vb[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#3)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#3)]

### <a name="to-insert-text-into-a-word-table"></a>Para insertar texto en una tabla de Word

1. Agregue el código siguiente al <xref:System.Windows.Forms.Control.Click> controlador de eventos del botón **Insertar** .

     [!code-vb[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb#4)]
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#4)]

2. En C#, debe crear un controlador de eventos para el <xref:System.Windows.Forms.Control.Click> evento del botón.  Este código se puede colocar en el <xref:System.Windows.Forms.UserControl.Load> controlador de eventos de la `ActionsControl` clase.

     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs#5)]

## <a name="show-the-actions-pane"></a>Mostrar el panel de acciones
 El panel de acciones se vuelve visible cuando se agregan controles a él.

### <a name="to-show-the-actions-pane"></a>Para mostrar el panel de acciones

1. En **Explorador de soluciones**, haga clic con el botón secundario en **ThisDocument. VB** o **ThisDocument.CS** y, a continuación, haga clic en **Ver código** en el menú contextual.

2. Cree una nueva instancia del control en la parte superior de la `ThisDocument` clase para que tenga un aspecto similar al ejemplo siguiente.

     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#6)]

3. Agregue código al <xref:Microsoft.Office.Tools.Word.Document.Startup> controlador de eventos de `ThisDocument` para que sea similar al ejemplo siguiente.

     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#7)]

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el documento para comprobar que el panel de acciones aparece cuando se abre el documento. Pruebe la relación principal-detalle en los controles del panel de acciones y asegúrese de que los datos se rellenan en una tabla de Word cuando se hace clic en el botón **Insertar** .

### <a name="to-test-your-document"></a>Para probar el documento

1. Presione **F5** para ejecutar el proyecto.

2. Confirme que el panel de acciones está visible.

3. Seleccione una compañía en el cuadro combinado y compruebe que los elementos del cuadro de lista **productos** cambian.

4. Seleccione un producto, haga clic en **Insertar** en el panel acciones y compruebe que los detalles del producto se agregan a la tabla de Word.

5. Inserte productos adicionales de varias empresas.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los conceptos básicos de enlazar datos a controles en un panel de acciones de Word. A continuación, podría realizar las siguientes tareas:

- Enlazar datos a controles en Excel. Para obtener más información, vea [Tutorial: enlazar datos a controles en un panel de acciones de Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).

- Implementar el proyecto. Para obtener más información, vea [implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Vea también
- [Información general del panel de acciones](../vsto/actions-pane-overview.md)
- [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
