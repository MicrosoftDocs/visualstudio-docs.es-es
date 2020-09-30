---
title: 'Tutorial: enlazar datos a controles en un panel de acciones de Excel'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3801aff53a5bf9a9a8d77263ab74127c1b2a9846
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585059"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Tutorial: enlazar datos a controles en un panel de acciones de Excel
  En este tutorial se muestra cómo enlazar datos a controles en un panel de acciones en Microsoft Office Excel. Los controles muestran una relación principal-detalle entre las tablas de una base de datos de SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Agregar controles a una hoja de cálculo.

- Crear un control del panel de acciones.

- Agregar controles de Windows Forms enlazados a datos a un control del panel de acciones.

- Mostrar el panel de acciones cuando se abra la aplicación.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acceso a un servidor con la base de datos de ejemplo Northwind SQL Server.

- Permisos para leer y escribir en la base de datos de SQL Server.

## <a name="create-the-project"></a>Crear el proyecto
 En primer lugar, es necesario crear un proyecto de libro de Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **mi panel de acciones de Excel**. En el asistente, seleccione **crear un nuevo documento**. Para obtener más información, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **Panel de acciones de Excel** a **Explorador de soluciones**.

## <a name="add-a-new-data-source-to-the-project"></a>Agregar un nuevo origen de datos al proyecto

### <a name="to-add-a-new-data-source-to-the-project"></a>Para agregar un nuevo origen de datos al proyecto

1. Si la ventana **orígenes de datos** no está visible, puede mostrarla en la barra de menús y elegir **Ver**  >  **otros**  >  **orígenes de datos**de Windows.

2. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. Seleccione **base de datos** y, a continuación, haga clic en **siguiente**.

4. Seleccione una conexión de datos a la base de datos de ejemplo Northwind SQL Server o agregue una nueva conexión mediante el botón **nueva conexión** .

5. Haga clic en **Siguiente**.

6. Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic en **siguiente**.

7. Expanda el nodo **tablas** en la ventana **objetos de base de datos** .

8. Active la casilla situada junto a la tabla **proveedores** .

9. Expanda la tabla **Products** y seleccione **ProductName**, **SupplierID**, **QuantityPerUnit**y **UnitPrice**.

10. Haga clic en **Finalizar**

    El asistente agrega la tabla **proveedores** y la tabla **productos** a la ventana **orígenes de datos** . También agrega un conjunto de un objeto con tipo al proyecto que está visible en **Explorador de soluciones**.

## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo
 A continuación, agregue un <xref:Microsoft.Office.Tools.Excel.NamedRange> control y un <xref:Microsoft.Office.Tools.Excel.ListObject> control a la primera hoja de cálculo.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Para agregar un control NamedRange y un control ListObject

1. Compruebe que las **acciones de Excel Pane.xlsx** libro está abierto en el diseñador de Visual Studio, con la que se `Sheet1` muestra.

2. En la ventana **orígenes de datos** , expanda la tabla **proveedores** .

3. Haga clic en la flecha desplegable del nodo nombre de la **compañía** y, a continuación, haga clic en **NamedRange**.

4. Arrastre **Company Name** desde la ventana **orígenes de datos** hasta la celda **a2** en `Sheet1` .

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Se crea un control denominado `CompanyNameNamedRange` y el texto \<CompanyName> aparece en la celda **a2**. Al mismo tiempo, <xref:System.Windows.Forms.BindingSource> `suppliersBindingSource` <xref:System.Data.DataSet> se agregan al proyecto un denominado, un adaptador de tabla y un. El control está enlazado a <xref:System.Windows.Forms.BindingSource> , que a su vez se enlaza a la <xref:System.Data.DataSet> instancia de.

5. En la ventana **orígenes de datos** , desplácese hacia abajo más allá de las columnas que se encuentran en la tabla **Suppliers** . En la parte inferior de la lista se encuentra la tabla **Products** ; Esto se debe a que es un elemento secundario de la tabla **Suppliers** . Seleccione esta tabla de **productos** , no la que se encuentra en el mismo nivel que la tabla **proveedores** y, a continuación, haga clic en la flecha desplegable que aparece.

6. Haga clic en **ListObject** en la lista desplegable y, a continuación, arrastre la tabla **Products** hasta la celda **A6** en `Sheet1` .

     <xref:Microsoft.Office.Tools.Excel.ListObject>Se crea un control denominado `ProductNameListObject` en la celda **A6**. Al mismo tiempo, <xref:System.Windows.Forms.BindingSource> `productsBindingSource` se agregan al proyecto un nombre y un adaptador de tabla. El control está enlazado a <xref:System.Windows.Forms.BindingSource> , que a su vez se enlaza a la <xref:System.Data.DataSet> instancia de.

7. Solo para C#, seleccione **suppliersBindingSource** en la bandeja de componentes y cambie la propiedad **Modificadores** a **interno** en la ventana **propiedades** .

## <a name="add-controls-to-the-actions-pane"></a>Agregar controles al panel de acciones
 A continuación, necesita un control del panel de acciones que tenga un cuadro combinado.

### <a name="to-add-an-actions-pane-control"></a>Para agregar un control del panel de acciones

1. Seleccione el proyecto **mi panel de acciones de Excel** en **Explorador de soluciones**.

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **control del panel de acciones**, asígnele el nombre **ActionsControl**y haga clic en **Agregar**.

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Para agregar controles de Windows Forms enlazados a datos a un control del panel de acciones

1. Desde las pestañas **controles comunes** del **cuadro de herramientas**, arrastre un <xref:System.Windows.Forms.ComboBox> control hasta el control panel de acciones.

2. Cambie la propiedad **size** a **171, 21**.

3. Cambie el tamaño del control de usuario para que se ajuste al cuadro combinado.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Enlazar el control del panel de acciones a los datos
 En esta sección, establecerá el origen de datos de <xref:System.Windows.Forms.ComboBox> en el mismo origen de datos que el <xref:Microsoft.Office.Tools.Excel.NamedRange> control de la hoja de cálculo.

### <a name="to-set-data-binding-properties-of-the-control"></a>Para establecer las propiedades de enlace de datos del control

1. Haga clic con el botón secundario en el control del panel de acciones y luego haga clic en **Ver código**.

2. Agregue el código siguiente al <xref:System.Windows.Forms.UserControl.Load> evento del control del panel de acciones.

     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]

3. En C#, debe crear un controlador de eventos para `ActionsControl` . Este código se puede colocar en el `ActionsControl` constructor. Para obtener más información sobre cómo crear controladores de eventos, consulte [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]

## <a name="show-the-actions-pane"></a>Mostrar el panel de acciones
 El panel de acciones no es visible hasta que se agrega el control en tiempo de ejecución.

#### <a name="to-show-the-actions-pane"></a>Para mostrar el panel de acciones

1. En **Explorador de soluciones**, haga clic con el botón secundario en *ThisWorkbook. VB* o *ThisWorkbook.CS*y, a continuación, haga clic en **Ver código**.

2. Cree una nueva instancia del control de usuario en la `ThisWorkbook` clase.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]

3. En el <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> controlador de eventos de `ThisWorkbook` , agregue el control al panel de acciones.

     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el documento para comprobar que el panel de acciones se abre cuando se abre el documento y que los controles tienen una relación principal-detalle.

### <a name="to-test-your-document"></a>Para probar el documento

1. Presione **F5** para ejecutar el proyecto.

2. Confirme que el panel de acciones está visible.

3. Seleccione una compañía en el cuadro de lista. Compruebe que el nombre de la empresa aparece en el <xref:Microsoft.Office.Tools.Excel.NamedRange> control y que los detalles del producto se muestran en el <xref:Microsoft.Office.Tools.Excel.ListObject> control.

4. Seleccione varias empresas para comprobar que el nombre de la empresa y los detalles del producto cambian según corresponda.

## <a name="next-steps"></a>Pasos siguientes
 A continuación, podría realizar las siguientes tareas:

- Enlazar datos a controles de Word. Para obtener más información, vea [Tutorial: enlazar datos a controles en un panel de acciones de Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

- Implementar el proyecto. Para obtener más información, vea [implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="see-also"></a>Vea también
- [Información general del panel de acciones](../vsto/actions-pane-overview.md)
- [Cómo: administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
