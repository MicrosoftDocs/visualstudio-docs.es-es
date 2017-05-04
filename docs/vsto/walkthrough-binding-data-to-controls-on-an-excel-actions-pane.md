---
title: "Tutorial: Enlazar datos a controles en un panel de acciones de Excel | Microsoft Docs"
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
  - "paneles de acciones [desarrollo de Office en Visual Studio], enlazar controles"
  - "paneles de acciones [desarrollo de Office en Visual Studio], enlace de datos"
  - "controles [desarrollo de Office en Visual Studio], enlace de datos"
  - "enlace de datos [desarrollo de Office en Visual Studio], paneles de acciones"
  - "enlace de datos [desarrollo de Office en Visual Studio], documentos inteligentes"
  - "documentos inteligentes [desarrollo de Office en Visual Studio], enlace de datos"
ms.assetid: 106c07bd-e931-4dc5-94dc-ca43900fe09d
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Tutorial: Enlazar datos a controles en un panel de acciones de Excel
  En este tutorial se muestra cómo enlazar datos a los controles en un panel de acciones de Microsoft Office Excel.  Los controles muestran una relación principal\-detalle entre las tablas de una base de datos de SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar controles a una hoja de cálculo.  
  
-   Crear un control del panel de acciones.  
  
-   Agregar controles de formularios Windows Forms enlazados a datos a un control del panel de acciones.  
  
-   Mostrar el panel de acciones cuando se abra la aplicación.  
  
> [!NOTE]  
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté usando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acceso a un servidor con la base de datos de ejemplo Northwind de SQL Server.  
  
-   Permisos de lectura y escritura en la base de datos de SQL Server.  
  
## Crear el proyecto  
 El primer paso es crear un proyecto de libro de Excel.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre Mi panel de acciones de Excel.  En el asistente, seleccione **Crear un nuevo documento**.  Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **Mi panel de acciones de Excel** al **Explorador de soluciones**.  
  
## Agregar un nuevo origen de datos al proyecto  
  
#### Para agregar un nuevo origen de datos al proyecto  
  
1.  Si la ventana **orígenes de datos** no está visible, muéstrela por, en la barra de menús, eligiendo **Vista**, **Otras ventanas**, **orígenes de datos**.  
  
2.  Elija **Agregar nuevo origen de datos** para iniciar **Asistente para la configuración de orígenes de datos**.  
  
3.  Seleccione **Base de datos** y, a continuación, haga clic en **Siguiente**.  
  
4.  Seleccione una conexión de datos a la base de datos de ejemplo Northwind de SQL Server o agregue una nueva conexión mediante el botón **Nueva conexión**.  
  
5.  Haga clic en **Siguiente**.  
  
6.  Si estuviera activada, desactive la opción de guardar la conexión y, a continuación, haga clic en **Siguiente**.  
  
7.  Expanda el nodo **Tablas** en la ventana **Objetos de base de datos**.  
  
8.  Active la casilla que aparece junto a la tabla **Proveedores**.  
  
9. Expanda la tabla **Productos** y seleccione **NombreProducto**, **IdProveedor**, **CantidadPorUnidad** y **PrecioUnidad**.  
  
10. Haga clic en **Finalizar**.  
  
 El asistente agrega las tablas **Suppliers** y **Products** a la ventana **Orígenes de datos**.  También agrega al proyecto un conjunto de datos con tipo, visible en el **Explorador de soluciones**.  
  
## Agregar controles a la hoja de cálculo  
 A continuación, agregue un control <xref:Microsoft.Office.Tools.Excel.NamedRange> y un control <xref:Microsoft.Office.Tools.Excel.ListObject> a la primera hoja de cálculo.  
  
#### Para agregar un control NamedRange y un control ListObject  
  
1.  Compruebe que el libro **Mis acciones Pane.xlsx de Excel** está abierto en el diseñador de Visual Studio, con `Sheet1` mostrados.  
  
2.  En la ventana **Orígenes de datos**, expanda la tabla **Suppliers**.  
  
3.  Haga clic en la flecha de la lista desplegable del nodo **Nombre de la organización** y, a continuación, haga clic en **NamedRange**.  
  
4.  Arrastre **Nombre de la organización** desde la ventana **Orígenes de datos** hasta la celda **A2** de la hoja `Sheet1`.  
  
     Se crea control <xref:Microsoft.Office.Tools.Excel.NamedRange> llamado `CompanyNameNamedRange` y en la celda **A2** aparece el texto \<NombreOrganización\>.  Al mismo tiempo, se agregan al proyecto un <xref:System.Windows.Forms.BindingSource> llamado `suppliersBindingSource`, un adaptador de la tabla y un <xref:System.Data.DataSet>.  El control se enlaza a <xref:System.Windows.Forms.BindingSource>, que, a su vez, se enlaza a la instancia de <xref:System.Data.DataSet>.  
  
5.  En la ventana **Orígenes de datos**, desplácese hacia abajo hasta más allá de las columnas situadas bajo la tabla **Proveedores**.  En la parte inferior de la lista se encuentra la tabla **Productos**; está ahí porque es un elemento secundario de la tabla **Proveedores**.  Seleccione esta tabla **Productos**, no la que está en el mismo nivel de la tabla **Proveedores** y, a continuación, haga clic en la flecha de la lista desplegable que aparece.  
  
6.  Haga clic en **ListObject** en la lista desplegable y, a continuación, arrastre la tabla **Productos** hasta la celda **A6** en `Sheet1`.  
  
     En la celda **A6** se crea un control <xref:Microsoft.Office.Tools.Excel.ListObject> llamado `ProductNameListObject`.  Al mismo tiempo, se agregan al proyecto un <xref:System.Windows.Forms.BindingSource> denominado `productsBindingSource` y un adaptador de la tabla.  El control se enlaza a <xref:System.Windows.Forms.BindingSource>, que, a su vez, se enlaza a la instancia de <xref:System.Data.DataSet>.  
  
7.  Para C\# únicamente, seleccione **suppliersBindingSource** en la bandeja de componentes y cambie la propiedad **Modifiers** a Internal en la ventana **Propiedades**.  
  
## Agregar controles al panel de acciones  
 A continuación, necesita un control del panel de acciones que contiene un cuadro combinado.  
  
#### Para agregar un control del panel de acciones  
  
1.  Seleccione el proyecto **Mi panel de acciones de Excel** en el **Explorador de soluciones**.  
  
2.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Control del panel de acciones**, asígnele el nombre **ActionsControl** y haga clic en **Agregar**.  
  
#### Para agregar controles de formularios Windows Forms enlazados a datos a un control del panel de acciones  
  
1.  En la ficha **Controles comunes** del **Cuadro de herramientas**, arrastre un control <xref:System.Windows.Forms.ComboBox> hasta el control del panel de acciones.  
  
2.  Cambie la propiedad **Size** a 171, 21.  
  
3.  Cambie el tamaño del control de usuario para ajustar el cuadro combinado.  
  
## Enlazar a datos el control del panel de acciones  
 En esta sección, establecerá el origen de datos de <xref:System.Windows.Forms.ComboBox> en el mismo origen de datos del control <xref:Microsoft.Office.Tools.Excel.NamedRange> de la hoja de cálculo.  
  
#### Para establecer propiedades de enlace de datos del control  
  
1.  Haga clic con el botón secundario en el control del panel de acciones y, a continuación, haga clic en **Ver código**.  
  
2.  Agregue el código siguiente al evento <xref:System.Windows.Forms.UserControl.Load> del control del panel de acciones.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ActionsControl.vb#1)]  
  
3.  En C\#, debe crear un controlador de eventos para `ActionsControl`.  Puede colocar este código en el constructor `ActionsControl`.  Para obtener información sobre cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ActionsControl.cs#2)]  
  
## Mostrar el panel de acciones  
 El panel de acciones no está visible hasta que se agrega el control en tiempo de ejecución.  
  
#### Para mostrar el panel de acciones  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en ThisWorkbook.vb o en ThisWorkbook.cs y, a continuación, haga clic en **Ver código**.  
  
2.  Cree una nueva instancia del control de usuario en la clase `ThisWorkbook`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#3)]  
  
3.  En el controlador de eventos <xref:Microsoft.Office.Tools.Excel.Workbook.Startup> de `ThisWorkbook`, agregue el control al panel de acciones.  
  
     [!code-csharp[Trin_VstcoreActionsPaneExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/CS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneExcel/VB/ThisWorkbook.vb#4)]  
  
## Probar la aplicación  
 Ahora puede probar su documento para comprobar que el panel de acciones se abre cuando se abre el documento y que el control tiene una relación principal\-detalle.  
  
#### Para probar el documento  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Confirme que el panel de acciones está visible.  
  
3.  Seleccione una organización en el cuadro de lista.  Compruebe que el nombre de la organización aparece en el control <xref:Microsoft.Office.Tools.Excel.NamedRange> y que los detalles del producto se muestran en el control <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
4.  Seleccione distintas organizaciones para comprobar que el nombre de la organización y los detalles del producto van cambiando en consecuencia.  
  
## Pasos siguientes  
 Éstas son algunas de las tareas que pueden venir a continuación:  
  
-   Enlazar datos a controles en Word.  Para obtener más información, vea [Tutorial: Enlazar datos a controles en un panel de acciones de Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
-   Implementar el proyecto.  Para obtener más información, vea [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Vea también  
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Cómo: Administrar el diseño de controles en paneles de acciones](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  