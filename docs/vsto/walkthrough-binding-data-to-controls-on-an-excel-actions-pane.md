---
title: 'Tutorial: Enlazar datos a controles en un panel de acciones de Excel'
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
ms.openlocfilehash: d90250abdf727e47bbc9049b00e15a0f2b7978a7
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865845"
---
# <a name="walkthrough-bind-data-to-controls-on-an-excel-actions-pane"></a>Tutorial: Enlazar datos a controles en un panel de acciones de Excel
  Este tutorial muestra el enlace de datos a controles en un panel de acciones en Microsoft Office Excel. Los controles muestran una relación principal-detalle entre las tablas de una base de datos de SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar controles a una hoja de cálculo.  
  
-   Creación de un control de panel de acciones.  
  
-   Agregar controles de Windows Forms enlazado a datos a un control de panel de acciones.  
  
-   Mostrar el panel de acciones cuando se abre la aplicación.  
  
> [!NOTE]  
>  Es posible que el equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones. La edición de Visual Studio que se tenga y la configuración que se utilice determinan estos elementos. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acceso a un servidor con la base de datos de ejemplo Northwind de SQL Server.  
  
-   Permisos para leer y escribir en la base de datos de SQL Server.  
  
## <a name="create-the-project"></a>Crear el proyecto  
 En primer lugar, es necesario crear un proyecto de libro de Excel.  
  
### <a name="to-create-a-new-project"></a>Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre **Mi panel de acciones de Excel**. En el asistente, seleccione **crear un nuevo documento**. Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el **Mi panel de acciones de Excel** proyecto a **el Explorador de soluciones**.  
  
## <a name="add-a-new-data-source-to-the-project"></a>Agregar un nuevo origen de datos al proyecto  
  
### <a name="to-add-a-new-data-source-to-the-project"></a>Para agregar un nuevo origen de datos al proyecto  
  
1. Si el **orígenes de datos** ventana no está visible, muéstrela; en la barra de menús, elija **vista** > **Other Windows**  >   **Orígenes de datos**.  
  
2. Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3. Seleccione **base de datos** y, a continuación, haga clic en **siguiente**.  
  
4. Seleccione una conexión de datos para la base de datos de SQL Server de ejemplo Northwind, o agregar una nueva conexión mediante el **nueva conexión** botón.  
  
5. Haga clic en **Siguiente**.  
  
6. Desactive la opción para guardar la conexión si está seleccionada y, a continuación, haga clic en **siguiente**.  
  
7. Expanda el **tablas** nodo en el **objetos de base de datos** ventana.  
  
8. Active la casilla situada junto a la **proveedores** tabla.  
  
9. Expanda el **productos** de tabla y seleccione **ProductName**, **SupplierID**, **QuantityPerUnit**, y **UnitPrice**.  
  
10. Haga clic en **Finalizar**.  
  
    El asistente agrega los **proveedores** tabla y **productos** la tabla a la **orígenes de datos** ventana. También agrega un conjunto de datos con tipo al proyecto que está visible en **el Explorador de soluciones**.  
  
## <a name="add-controls-to-the-worksheet"></a>Agregar controles a la hoja de cálculo  
 A continuación, agregue un <xref:Microsoft.Office.Tools.Excel.NamedRange> control y un <xref:Microsoft.Office.Tools.Excel.ListObject> control a la primera hoja de cálculo.  
  
### <a name="to-add-a-namedrange-control-and-a-listobject-control"></a>Para agregar un control NamedRange y un control ListObject  
  
1.  Compruebe que la **Pane.xlsx de acciones de Excel mi** libro está abierto en el Diseñador de Visual Studio, con `Sheet1` muestra.  
  
2.  En el **orígenes de datos** ventana, expanda el **proveedores** tabla.  
  
3.  Haga clic en la flecha de lista desplegable el **nombre de la compañía** nodo y, a continuación, haga clic en **NamedRange**.  
  
4.  Arrastre **nombre de la compañía** desde el **orígenes de datos** ventana a la celda **A2** en `Sheet1`.  
  
     Un <xref:Microsoft.Office.Tools.Excel.NamedRange> control denominado `CompanyNameNamedRange` se crea y el texto \<CompanyName > aparece en la celda **A2**. Al mismo tiempo, un <xref:System.Windows.Forms.BindingSource> denominado `suppliersBindingSource`, un adaptador de tabla y un <xref:System.Data.DataSet> se agregan al proyecto. El control se enlaza a la <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza a la <xref:System.Data.DataSet> instancia.  
  
5.  En el **orígenes de datos** ventana, desplácese hacia abajo más allá de las columnas que están bajo el **proveedores** tabla. En la parte inferior de la lista es la **productos** tabla; está aquí porque es un elemento secundario de la **proveedores** tabla. Seleccione esta opción **productos** de tabla, no lo que es el mismo nivel que el **proveedores** de tabla y, a continuación, haga clic en la flecha de lista desplegable que aparece.  
  
6.  Haga clic en **ListObject** en la lista desplegable y, a continuación, arrastre el **productos** tabla a la celda **A6** en `Sheet1`.  
  
     Un <xref:Microsoft.Office.Tools.Excel.ListObject> control denominado `ProductNameListObject` se crea en la celda **A6**. Al mismo tiempo, un <xref:System.Windows.Forms.BindingSource> denominado `productsBindingSource` y un adaptador de tabla se agregan al proyecto. El control se enlaza a la <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza a la <xref:System.Data.DataSet> instancia.  
  
7.  Solo en C#, seleccione **suppliersBindingSource** en la Bandeja de componentes y cambie el **modificadores** propiedad **interno** en la **propiedades** ventana.  
  
## <a name="add-controls-to-the-actions-pane"></a>Agregar controles al panel de acciones  
 A continuación, necesita un control de panel de acciones que contiene un cuadro combinado.  
  
### <a name="to-add-an-actions-pane-control"></a>Para agregar un control de panel de acciones  
  
1.  Seleccione el **Mi panel de acciones de Excel** proyecto **el Explorador de soluciones**.  
  
2.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
3.  En el **Agregar nuevo elemento** cuadro de diálogo, seleccione **Control Panel de acciones**, asígnele el nombre **ActionsControl**y haga clic en **agregar**.  
  
### <a name="to-add-data-bound-windows-forms-controls-to-an-actions-pane-control"></a>Para agregar controles de Windows Forms enlazado a datos a un control de panel de acciones  
  
1.  Desde el **controles comunes** pestañas de la **cuadro de herramientas**, arrastre un <xref:System.Windows.Forms.ComboBox> control al control del panel de acciones.  
  
2.  Cambiar el **tamaño** propiedad **171, 21**.  
  
3.  Cambiar el tamaño del control de usuario para ajustar el cuadro combinado.  
  
## <a name="bind-the-control-on-the-actions-pane-to-data"></a>Enlazar el control del panel de acciones a los datos  
 En esta sección, podrá establecer el origen de datos de la <xref:System.Windows.Forms.ComboBox> al mismo origen de datos como el <xref:Microsoft.Office.Tools.Excel.NamedRange> control en la hoja de cálculo.  
  
### <a name="to-set-data-binding-properties-of-the-control"></a>Establecer las propiedades de enlace de datos del control  
  
1.  Haga clic en el panel de acciones y, a continuación, haga clic en **ver código**.  
  
2.  Agregue el código siguiente a la <xref:System.Windows.Forms.UserControl.Load> eventos del control del panel de acciones.  
  
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ActionsControl.vb#1)]
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#1)]  
  
3.  En C#, debe crear un controlador de eventos para el `ActionsControl`. Puede colocar este código en el `ActionsControl` constructor. Para obtener más información acerca de cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ActionsControl.cs#2)]  
  
## <a name="show-the-actions-pane"></a>Mostrar el panel de acciones  
 El panel de acciones no es visible hasta que agregue el control en tiempo de ejecución.  
  
#### <a name="to-show-the-actions-pane"></a>Para mostrar el panel de acciones  
  
1.  En **el Explorador de soluciones**, haga clic en *ThisWorkbook.vb* o *ThisWorkbook.cs*y, a continuación, haga clic en **ver código**.  
  
2.  Crear una nueva instancia del control de usuario en el `ThisWorkbook` clase.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#3)]  
  
3.  En el <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> controlador de eventos de `ThisWorkbook`, agregue el control al panel de acciones.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneExcelCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneExcelVB/ThisWorkbook.vb#4)]  
  
## <a name="test-the-application"></a>Probar la aplicación  
 Ahora puede probar el documento para comprobar que se abre el panel de acciones cuando se abre el documento y que los controles tienen una relación principal-detalle.  
  
### <a name="to-test-your-document"></a>Para probar el documento  
  
1.  Presione **F5** para ejecutar el proyecto.  
  
2.  Confirme que el panel de acciones está visible.  
  
3.  Seleccione una empresa en el cuadro de lista. Compruebe que aparece el nombre de la empresa en el <xref:Microsoft.Office.Tools.Excel.NamedRange> control y que se muestran los detalles del producto en el <xref:Microsoft.Office.Tools.Excel.ListObject> control.  
  
4.  Seleccione distintas organizaciones para comprobar el nombre de la empresa y detalles del producto cambian según corresponda.  
  
## <a name="next-steps"></a>Pasos siguientes  
 A continuación, podría realizar las siguientes tareas:  
  
-   Enlazar datos a controles de Word. Para obtener más información, vea [Tutorial: Enlazar datos a controles en un panel de acciones de Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   Implementar el proyecto. Para obtener más información, consulte [implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre el panel de acciones](../vsto/actions-pane-overview.md)   
 [Cómo: Administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
