---
title: 'Tutorial: Enlazar datos a controles en un panel de acciones de Word'
description: Enlace de datos a controles en un panel de acciones en Microsoft Word. Los controles muestran una relación principal-detalle entre las tablas de una base de datos de SQL Server.
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
ms.openlocfilehash: d94891520695117c7a395f81feda81e52f909fe6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824502"
---
# <a name="walkthrough-bind-data-to-controls-on-a-word-actions-pane"></a>Tutorial: Enlazar datos a controles en un panel de acciones de Word
  En este tutorial se muestra el enlace de datos a controles en un panel de acciones en Word. Los controles muestran una relación principal-detalle entre las tablas de una base de datos de SQL Server.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Crear un panel de acciones con Windows Forms controles enlazados a datos.

- Usar una relación maestro-detalle para mostrar datos en los controles.

- Muestra el panel de acciones cuando se abre la aplicación.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

- Acceso a un servidor con la base de datos de ejemplo Northwind SQL Server ejemplo.

- Permisos para leer y escribir en la base de datos SQL Server datos.

## <a name="create-the-project"></a>Creación del proyecto
 El primer paso es crear un proyecto de tipo Documento de Word.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de documento de Word con el nombre **Panel acciones de Mi palabra**. En el asistente, seleccione **Crear un nuevo documento.**

     Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio el nuevo documento de Word en el diseñador y agrega el proyecto panel Acciones **de** Mi palabra **a Explorador de soluciones**.

## <a name="add-controls-to-the-actions-pane"></a>Agregar controles al panel de acciones
 Para este tutorial, necesita un control de panel de acciones que contenga controles de Windows Forms datos enlazados a datos. Agregue un origen de datos al proyecto y arrastre los controles desde la ventana **Orígenes de** datos al control del panel de acciones.

### <a name="to-add-an-actions-pane-control"></a>Para agregar un control de panel de acciones

1. Seleccione el **proyecto Panel de acciones de** Mi palabra **Explorador de soluciones**.

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el **cuadro de diálogo Agregar nuevo** elemento, seleccione Control del **panel** acciones , así mismo dele el nombre **ActionsControl** y, a continuación, haga clic **en Agregar**.

### <a name="to-add-a-data-source-to-the-project"></a>Para agregar un origen de datos al proyecto

1. Si la **ventana Orígenes de** datos no está visible, para mostrarla, en la barra de menús, elija **Ver** otros orígenes de  >  **datos** de Windows  >  .

   > [!NOTE]
   > Si **Mostrar orígenes de datos** no está disponible, haga clic en el documento de Word y vuelva a comprobarlo.

2. Haga clic **en Agregar nuevo origen de datos** para iniciar el Asistente para configuración del origen de **datos**.

3. Seleccione **Base de datos** y, a continuación, haga clic en **Siguiente.**

4. Seleccione una conexión de datos al ejemplo Northwind SQL Server base de datos o agregue una nueva conexión mediante el **botón Nueva** conexión.

5. Haga clic en **Next**.

6. Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic **en Siguiente.**

7. Expanda el nodo **Tablas** en la ventana **Objetos de base de** datos .

8. Active la casilla situada junto a **las tablas Proveedores** **y** Productos.

9. Haga clic en **Finalizar**

   El asistente agrega la **tabla Proveedores** y la tabla **Products a** la ventana **Orígenes de** datos. También agrega un conjunto de datos con tipo al proyecto que es visible **en Explorador de soluciones**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Para agregar controles de Windows Forms enlazados a datos a un control de panel de acciones

1. En la **ventana Orígenes de** datos, expanda la **tabla** Proveedores.

2. Haga clic en la flecha desplegable del **nodo Nombre de** la empresa y seleccione **ComboBox**.

3. Arrastre **CompanyName desde** la **ventana Orígenes de** datos hasta el control del panel de acciones.

     Se <xref:System.Windows.Forms.ComboBox> crea un control en el control del panel de acciones. Al mismo tiempo, se agregan un denominado , un adaptador de tabla y un <xref:System.Windows.Forms.BindingSource> al proyecto en la bandeja de `SuppliersBindingSource` <xref:System.Data.DataSet> componentes.

4. Seleccione `SuppliersBindingNavigator` en la bandeja **Componentes** y presione **Eliminar.** No usará en `SuppliersBindingNavigator` este tutorial.

    > [!NOTE]
    > Al eliminar `SuppliersBindingNavigator` no se quita todo el código que se generó para él. Puede quitar este código.

5. Mueva el cuadro combinado para que esté bajo la etiqueta y cambie la **propiedad Size** a **171, 21**.

6. En la **ventana Orígenes de** datos, expanda la tabla **Products** que es un elemento secundario de la **tabla Suppliers.**

7. Haga clic en la flecha desplegable del **nodo ProductName** y seleccione **ListBox**.

8. Arrastre **ProductName** al control del panel de acciones.

     Se <xref:System.Windows.Forms.ListBox> crea un control en el control del panel de acciones. Al mismo tiempo, se agregan un adaptador con nombre y un adaptador de tabla <xref:System.Windows.Forms.BindingSource> al proyecto en la bandeja de `ProductBindingSource` componentes.

9. Mueva el cuadro de lista para que esté bajo la etiqueta y cambie la **propiedad Size** a **171,95**.

10. Arrastre un <xref:System.Windows.Forms.Button> desde el cuadro de **herramientas** hasta el control del panel de acciones y colótrelo debajo del cuadro de lista.

11. Haga clic con el botón derecho en , haga clic en Propiedades en <xref:System.Windows.Forms.Button> el menú contextual y cambie las siguientes propiedades. 

    |Propiedad|Value|
    |--------------|-----------|
    |**Nombre**|**Insertar**|
    |**Texto**|**Insertar**|

12. Cambie el tamaño del control de usuario para que se ajuste a los controles.

## <a name="set-up-the-data-source"></a>Configuración del origen de datos
 Para configurar el origen de datos, agregue código al evento del control del panel de acciones para rellenar el control con datos de y establezca las propiedades <xref:System.Windows.Forms.UserControl.Load> <xref:System.Data.DataTable> y de cada <xref:System.Windows.Forms.Binding.DataSource%2A> <xref:System.Windows.Forms.BindingSource.DataMember%2A> control.

### <a name="to-load-the-control-with-data"></a>Para cargar el control con datos

1. En el <xref:System.Windows.Forms.UserControl.Load> controlador de eventos de la clase , agregue el código `ActionsControl` siguiente.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet1":::

2. En C#, debe adjuntar el controlador de eventos al <xref:System.Windows.Forms.UserControl.Load> evento. Puede colocar este código en el `ActionsControl` constructor, después de la llamada a `InitializeComponent` . Para obtener más información sobre cómo crear controladores de eventos, [vea Cómo: Crear controladores de eventos en proyectos de Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet33":::

### <a name="to-set-data-binding-properties-of-the-controls"></a>Para establecer las propiedades de enlace de datos de los controles

1. Seleccione el control `CompanyNameComboBox`.

2. En la **ventana** Propiedades, haga clic en el botón situado a la derecha de la **propiedad DataSource** y seleccione **suppliersBindingSource**.

3. Haga clic en el botón situado a la derecha de la **propiedad DisplayMember** y seleccione **CompanyName**.

4. Expanda la **propiedad DataBindings,** haga clic en el botón situado a la derecha de la **propiedad Text** y seleccione **Ninguno.**

5. Seleccione el control `ProductNameListBox`.

6. En la **ventana Propiedades,** haga clic en el botón situado a la derecha de la **propiedad DataSource** y seleccione **productsBindingSource**.

7. Haga clic en el botón situado a la derecha de la **propiedad DisplayMember** y seleccione **ProductName**.

8. Expanda la **propiedad DataBindings,** haga clic en el botón situado a la derecha de la **propiedad SelectedValue** y seleccione **Ninguno.**

## <a name="add-a-method-to-insert-data-into-a-table"></a>Agregar un método para insertar datos en una tabla
 La siguiente tarea consiste en leer los datos de los controles enlazados y rellenar una tabla en el documento de Word. En primer lugar, cree un procedimiento para dar formato a los encabezados de la tabla y, a continuación, agregue el método para crear y dar formato `AddData` a una tabla de Word.

### <a name="to-format-the-table-headings"></a>Para dar formato a los encabezados de tabla

1. En la `ActionsControl` clase , cree un método para dar formato a los encabezados de la tabla.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet2":::

### <a name="to-create-the-table"></a>Para crear la tabla

1. En la clase , escriba un método que creará una tabla si aún no existe y agregue datos desde el panel de acciones `ActionsControl` a la tabla.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet3":::

### <a name="to-insert-text-into-a-word-table"></a>Para insertar texto en una tabla de Word

1. Agregue el código siguiente al controlador <xref:System.Windows.Forms.Control.Click> de eventos del botón **Insertar.**

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ActionsControl.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet4":::

2. En C#, debe crear un controlador de eventos para <xref:System.Windows.Forms.Control.Click> el evento del botón.  Puede colocar este código en el controlador <xref:System.Windows.Forms.UserControl.Load> de eventos de la clase `ActionsControl` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ActionsControl.cs" id="Snippet5":::

## <a name="show-the-actions-pane"></a>Mostrar el panel de acciones
 El panel de acciones se vuelve visible después de que se le agregan controles.

### <a name="to-show-the-actions-pane"></a>Para mostrar el panel de acciones

1. En **Explorador de soluciones**, haga clic con el botón derecho en **ThisDocument.vb** o **ThisDocument.cs** y, a continuación, haga clic en Ver código **en** el menú contextual.

2. Cree una nueva instancia del control en la parte superior de la clase para que se parezca `ThisDocument` al ejemplo siguiente.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet6":::

3. Agregue código al controlador <xref:Microsoft.Office.Tools.Word.Document.Startup> de eventos de para que se parezca al ejemplo `ThisDocument` siguiente.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet7":::

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el documento para comprobar que el panel de acciones aparece cuando se abre el documento. Pruebe la relación maestro-detalle en los controles del panel de acciones y asegúrese de  que los datos se rellenan en una tabla de Word cuando se hace clic en el botón Insertar.

### <a name="to-test-your-document"></a>Para probar el documento

1. Presione **F5** para ejecutar el proyecto.

2. Confirme que el panel de acciones está visible.

3. Seleccione una empresa en el cuadro combinado y compruebe que los elementos del cuadro de lista **Productos** cambian.

4. Seleccione un producto, haga clic **en Insertar** en el panel de acciones y compruebe que los detalles del producto se agregan a la tabla en Word.

5. Inserte productos adicionales de varias empresas.

## <a name="next-steps"></a>Pasos siguientes
 En este tutorial se muestran los conceptos básicos del enlace de datos a controles en un panel de acciones en Word. A continuación, podría realizar las siguientes tareas:

- Enlazar datos a controles de Excel. Para obtener más información, vea [Tutorial: Enlazar datos a controles en un panel de acciones de Excel.](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md)

- Implementación del proyecto. Para obtener más información, vea [Implementar una solución de Office mediante ClickOnce.](../vsto/deploying-an-office-solution-by-using-clickonce.md)

## <a name="see-also"></a>Consulte también
- [Información general del panel Acciones](../vsto/actions-pane-overview.md)
- [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
