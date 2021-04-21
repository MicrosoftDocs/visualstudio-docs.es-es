---
title: 'Tutorial: Enlazar datos a controles en un panel de acciones de Excel'
description: Enlazar datos a controles en un panel de acciones en Microsoft Excel. Los controles muestran una relación principal-detalle entre las tablas de una base de datos de SQL Server.
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
ms.openlocfilehash: 377c3405211c91712f8754131d8379c3dae7e820
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824554"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Tutorial: Enlazar datos a controles en un panel de acciones de Excel
  En este tutorial se muestra el enlace de datos a controles en un panel de acciones Microsoft Office Excel. Los controles muestran una relación principal-detalle entre las tablas de una base de datos de SQL Server.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 En este tutorial se muestran las tareas siguientes:

- Agregar controles a una hoja de cálculo.

- Crear un control de panel de acciones.

- Agregar controles de Windows Forms enlazados a datos a un control de panel de acciones.

- Mostrar el panel de acciones cuando se abre la aplicación.

> [!NOTE]
> Es posible que tu equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Requisitos previos
 Necesitará los componentes siguientes para completar este tutorial:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acceso a un servidor con la base de datos de ejemplo Northwind SQL Server ejemplo.

- Permisos para leer y escribir en la base de datos SQL Server datos.

## <a name="create-the-project"></a>Creación del proyecto
 En primer lugar, es necesario crear un proyecto de libro de Excel.

### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto

1. Cree un proyecto de libro de Excel con el nombre **Panel De acciones de Excel.** En el asistente, seleccione **Crear un nuevo documento.** Para obtener más información, [vea Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto Panel De **acciones de Excel** a **Explorador de soluciones**.

## <a name="add-a-new-data-source-to-the-project"></a>Agregar un nuevo origen de datos al proyecto

### <a name="to-add-a-new-data-source-to-the-project"></a>Para agregar un nuevo origen de datos al proyecto

1. Si la **ventana Orígenes de** datos no está visible, para mostrarla, en la barra de menús, elija **Ver** otros orígenes de  >  **datos** de Windows  >  .

2. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

3. Seleccione **Base de datos** y, a continuación, haga clic en **Siguiente.**

4. Seleccione una conexión de datos al ejemplo Northwind SQL Server base de datos o agregue una nueva conexión mediante el **botón Nueva** conexión.

5. Haga clic en **Next**.

6. Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic **en Siguiente.**

7. Expanda el nodo **Tablas** en la ventana **Objetos de base de** datos .

8. Active la casilla situada junto a la **tabla Proveedores.**

9. Expanda la **tabla Products** y seleccione **ProductName**, **SupplierID,** **QuantityPerUnit** y **UnitPrice.**

10. Haga clic en **Finalizar**

    El asistente agrega la **tabla Proveedores y** la tabla Products **a** la ventana **Orígenes de** datos. También agrega un conjunto de datos con tipo al proyecto que está visible en **Explorador de soluciones**.

## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo
 A continuación, agregue <xref:Microsoft.Office.Tools.Excel.NamedRange> un control y un control a la primera hoja de <xref:Microsoft.Office.Tools.Excel.ListObject> cálculo.

### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Para agregar un control NamedRange y un control ListObject

1. Compruebe que el libro My Excel Actions Pane.xlsx(Mis acciones de **Excel)** está abierto en el diseñador Visual Studio, `Sheet1` con la vista mostrada.

2. En la **ventana Orígenes de** datos, expanda la **tabla** Proveedores.

3. Haga clic en la flecha desplegable del **nodo Nombre de** la empresa y, a continuación, haga clic en **NamedRange**.

4. Arrastre **Company Name (Nombre de** la compañía) desde la ventana Orígenes **de** datos a la **celda A2** en `Sheet1` .

     Se <xref:Microsoft.Office.Tools.Excel.NamedRange> crea un control denominado y el texto aparece en la celda `CompanyNameNamedRange` \<CompanyName> **A2.** Al mismo tiempo, se agregan al proyecto un denominado , un adaptador de <xref:System.Windows.Forms.BindingSource> `suppliersBindingSource` tabla y un <xref:System.Data.DataSet> . El control está enlazado a , que a su <xref:System.Windows.Forms.BindingSource> vez está enlazado a la instancia de <xref:System.Data.DataSet> .

5. En la **ventana Orígenes de** datos, desplácese hacia abajo más allá de las columnas que se encuentran en la **tabla** Proveedores. En la parte inferior de la lista se encuentra la **tabla Products;** aquí porque es un elemento secundario de la **tabla Suppliers.** Seleccione esta **tabla Productos,** no la que está en el mismo nivel que la tabla **Proveedores** y, a continuación, haga clic en la flecha desplegable que aparece.

6. Haga **clic en ListObject** en la lista desplegable y arrastre la **tabla Products** a la **celda A6** en `Sheet1` .

     Se <xref:Microsoft.Office.Tools.Excel.ListObject> crea un control denominado en la celda `ProductNameListObject` **A6.** Al mismo tiempo, se agregan al proyecto un adaptador con nombre y un <xref:System.Windows.Forms.BindingSource> `productsBindingSource` adaptador de tabla. El control está enlazado a , que a su <xref:System.Windows.Forms.BindingSource> vez está enlazado a la instancia de <xref:System.Data.DataSet> .

7. Solo para C#, seleccione **suppliersBindingSource** en la bandeja de componentes y cambie la propiedad **Modificadores** a **Interno** en la **ventana** Propiedades.

## <a name="add-controls-to-the-actions-pane"></a>Agregar controles al panel de acciones
 A continuación, necesita un control de panel de acciones que tenga un cuadro combinado.

### <a name="to-add-an-actions-pane-control"></a>Para agregar un control de panel de acciones

1. Seleccione el **proyecto Panel De acciones de Excel** en **Explorador de soluciones**.

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el **cuadro de diálogo Agregar nuevo** elemento, seleccione Control del **panel** acciones , así mismo dele el **nombre ActionsControl** y haga clic en **Agregar.**

### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Para agregar controles de Windows Forms enlazados a datos a un control del panel de acciones

1. En las **pestañas Controles** comunes del Cuadro **de** herramientas , arrastre un control al <xref:System.Windows.Forms.ComboBox> control del panel de acciones.

2. Cambie la **propiedad Size** a **171, 21**.

3. Cambie el tamaño del control de usuario para que se ajuste al cuadro combinado.

## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Enlazar el control del panel de acciones a los datos
 En esta sección, establecerá el origen de datos de en el mismo origen de datos <xref:System.Windows.Forms.ComboBox> que el control de la hoja de <xref:Microsoft.Office.Tools.Excel.NamedRange> cálculo.

### <a name="to-set-data-binding-properties-of-the-control"></a>Para establecer las propiedades de enlace de datos del control

1. Haga clic con el botón derecho en el control del panel de acciones y, a continuación, haga clic **en Ver código.**

2. Agregue el código siguiente al evento <xref:System.Windows.Forms.UserControl.Load> del control del panel de acciones.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs" id="Snippet1":::

3. En C#, debe crear un controlador de eventos para `ActionsControl` . Puede colocar este código en el `ActionsControl` constructor . Para obtener más información sobre cómo crear controladores de eventos, [vea Cómo: Crear controladores de eventos en proyectos de Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs" id="Snippet2":::

## <a name="show-the-actions-pane"></a>Mostrar el panel de acciones
 El panel de acciones no está visible hasta que agregue el control en tiempo de ejecución.

#### <a name="to-show-the-actions-pane"></a>Para mostrar el panel de acciones

1. En **Explorador de soluciones**, haga clic con el botón derecho en *ThisWorkbook.vb o* *ThisWorkbook.cs* y, a continuación, haga clic **en Ver código**.

2. Cree una nueva instancia del control de usuario en la `ThisWorkbook` clase .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet3":::

3. En el <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> controlador de eventos de , agregue el control al panel de `ThisWorkbook` acciones.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb" id="Snippet4":::

## <a name="test-the-application"></a>Prueba de la aplicación
 Ahora puede probar el documento para comprobar que el panel de acciones se abre cuando se abre el documento y que los controles tienen una relación maestro-detalle.

### <a name="to-test-your-document"></a>Para probar el documento

1. Presione **F5** para ejecutar el proyecto.

2. Confirme que el panel de acciones está visible.

3. Seleccione una empresa en el cuadro de lista. Compruebe que el nombre de la empresa aparece en el <xref:Microsoft.Office.Tools.Excel.NamedRange> control y que los detalles del producto aparecen en el <xref:Microsoft.Office.Tools.Excel.ListObject> control.

4. Seleccione varias empresas para comprobar que el nombre de la empresa y los detalles del producto cambian según corresponda.

## <a name="next-steps"></a>Pasos siguientes
 A continuación, podría realizar las siguientes tareas:

- Enlazar datos a controles de Word. Para obtener más información, vea [Tutorial: Enlazar datos a controles en un panel de acciones de Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

- Implementación del proyecto. Para obtener más información, vea [Implementar una solución de Office mediante ClickOnce.](../vsto/deploying-an-office-solution-by-using-clickonce.md)

## <a name="see-also"></a>Consulte también
- [Información general del panel Acciones](../vsto/actions-pane-overview.md)
- [Cómo: Administrar el diseño de control en los paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Enlace de datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)
