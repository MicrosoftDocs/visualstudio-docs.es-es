---
title: "Tutorial: Enlazar datos a controles en un panel de acciones de Word | Microsoft Docs"
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
ms.assetid: 5ef72fc7-412b-4454-9890-4479a13ee7f9
caps.latest.revision: 64
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 63
---
# Tutorial: Enlazar datos a controles en un panel de acciones de Word
  Este tutorial se muestra cómo enlazar datos a controles en un panel de acciones de word.  Los controles muestran una relación principal\-detalle entre las tablas de una base de datos de SQL Server.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un panel de acciones con controles de formularios Windows Forms enlazados a datos.  
  
-   Utilizar una relación principal\-detalle para mostrar datos en los controles.  
  
-   Mostrar el panel de acciones cuando se abre la aplicación.  
  
> [!NOTE]  
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté usando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Acceso a un servidor con la base de datos de ejemplo Northwind de SQL Server.  
  
-   Permisos de lectura y escritura en la base de datos de SQL Server.  
  
## Crear el proyecto  
 El primer paso es crear el proyecto de documento de Word.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de documento de Word con el nombre Mi panel de acciones de Word.  En el asistente, seleccione **Crear un nuevo documento**.  
  
     Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo documento de Word en el diseñador y agrega el proyecto **Mi panel de acciones de Word** al **Explorador de soluciones**.  
  
## Agregar controles al panel de acciones  
 Para este tutorial, necesitará un control del panel de acciones que contenga controles de formularios Windows Forms enlazados a datos.  Agregue un origen de datos al proyecto y, a continuación, arrastre los controles de la ventana **Orígenes de datos** al control del panel de acciones.  
  
#### Para agregar un control del panel de acciones  
  
1.  Seleccione el proyecto **Mi panel de acciones de Word** en el **Explorador de soluciones**.  
  
2.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento**, seleccione **Control del panel de acciones**, asígnele el nombre **ActionsControl** y, a continuación, haga clic en **Agregar**.  
  
#### Para agregar un código fuente al proyecto  
  
1.  Si la ventana **orígenes de datos** no está visible, muéstrela por, en la barra de menús, eligiendo **Vista**, **Otras ventanas**, **orígenes de datos**.  
  
    > [!NOTE]  
    >  Si la opción **Mostrar orígenes de datos** no está disponible, haga clic en el documento de Word y compruébelo de nuevo.  
  
2.  Haga clic en **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Seleccione **Base de datos** y, a continuación, haga clic en **Siguiente**.  
  
4.  Seleccione una conexión de datos a la base de datos de ejemplo Northwind de SQL Server o agregue una nueva conexión mediante el botón **Nueva conexión**.  
  
5.  Haga clic en **Siguiente**.  
  
6.  Si estuviera activada, desactive la opción de guardar la conexión y, a continuación, haga clic en **Siguiente**.  
  
7.  Expanda el nodo **Tablas** en la ventana **Objetos de base de datos**.  
  
8.  Active la casilla situada junto a las tablas **Suppliers** y **Products**.  
  
9. Haga clic en **Finalizar**.  
  
 El asistente agrega las tablas **Suppliers** y **Products** a la ventana **Orígenes de datos**.  También agrega al proyecto un conjunto de datos con tipo, visible en el **Explorador de soluciones**.  
  
#### Para agregar controles de formularios Windows Forms enlazados a datos a un control del panel de acciones  
  
1.  En la ventana **Orígenes de datos**, expanda la tabla **Suppliers**.  
  
2.  Haga clic en la flecha de lista desplegable en el nodo **Company Name** y seleccione **ComboBox**.  
  
3.  Arrastre **CompanyName** desde la ventana **Orígenes de datos** al control del panel de acciones.  
  
     A continuación, se creará un control <xref:System.Windows.Forms.ComboBox> en el control del panel de acciones.  Al mismo tiempo se agregarán al proyecto, en la bandeja de componentes, un control <xref:System.Windows.Forms.BindingSource> denominado `SuppliersBindingSource`, un adaptador de tablas y una clase <xref:System.Data.DataSet>.  
  
4.  Seleccione `SuppliersBindingNavigator` en la bandeja de componentes y presione SUPRIMIR.  No utilizará `SuppliersBindingNavigator` en este tutorial.  
  
    > [!NOTE]  
    >  Al eliminar `SuppliersBindingNavigator`, no se elimina todo el código generado para él.  Puede quitar este código.  
  
5.  Mueva el cuadro combinado hasta que se encuentre bajo la etiqueta y cambie la propiedad **Size** a 171, 21.  
  
6.  En la ventana **Orígenes de datos**, expanda la tabla **Products** que es secundaria de la tabla **Suppliers**.  
  
7.  Haga clic en la flecha de lista desplegable en el nodo **ProductName** y seleccione **ListBox**.  
  
8.  Arrastre **ProductName** al control del panel de acciones.  
  
     A continuación, se creará un control <xref:System.Windows.Forms.ListBox> en el control del panel de acciones.  Al mismo tiempo se agregarán al proyecto, en la bandeja de componentes, un control <xref:System.Windows.Forms.BindingSource> denominado `ProductBindingSource` y un adaptador de tablas.  
  
9. Mueva el cuadro de lista hasta que se encuentre bajo la etiqueta y cambie la propiedad **Size** a 171,95.  
  
10. Arrastre el control <xref:System.Windows.Forms.Button> desde el **Cuadro de herramientas** al control del panel de acciones y colóquelo debajo del cuadro de lista.  
  
11. Haga clic con el botón secundario en el control <xref:System.Windows.Forms.Button>, haga clic en **Propiedades**, en el menú contextual, y cambie las siguientes propiedades.  
  
    |Propiedad|Valor|  
    |---------------|-----------|  
    |**Nombre**|**Insert**|  
    |**Texto**|**Insert**|  
  
12. Cambie el tamaño del control de usuario para ajustar los controles.  
  
## Configurar el origen de datos  
 Para configurar el origen de datos, agregue código al evento <xref:System.Windows.Forms.UserControl.Load> del control del panel de acciones para rellenar el control con datos de la clase <xref:System.Data.DataTable> y establezca las propiedades <xref:System.Windows.Forms.Binding.DataSource%2A> y <xref:System.Windows.Forms.BindingSource.DataMember%2A> para cada control.  
  
#### Para cargar el control con datos  
  
1.  En el controlador de eventos <xref:System.Windows.Forms.UserControl.Load> de la clase `ActionsControl`, agregue el siguiente código.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#1)]
     [!code-vb[Trin_VstcoreActionsPaneWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#1)]  
  
2.  En C\#, debe asociar el controlador de eventos al evento <xref:System.Windows.Forms.UserControl.Load>.  Puede colocar este código en el constructor `ActionsControl`, después de la llamada a `InitializeComponent`.  Para obtener más información acerca de cómo crear controladores de eventos, vea [Cómo: Crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#33)]  
  
#### Para establecer las propiedades de enlace de datos de los controles  
  
1.  Seleccione el control `CompanyNameComboBox`.  
  
2.  En la ventana **Propiedades**, haga clic en el botón situado a la derecha de la propiedad **DataSource** y seleccione **suppliersBindingSource**.  
  
3.  Haga clic en el botón situado a la derecha de la propiedad **DisplayMember** y seleccione **CompanyName**.  
  
4.  Expanda la propiedad **DataBindings**, haga clic en el botón situado a la derecha de la propiedad **Text** y seleccione **Ninguno**.  
  
5.  Seleccione el control `ProductNameListBox`.  
  
6.  En la ventana **Propiedades**, haga clic en el botón situado a la derecha de la propiedad **DataSource** y seleccione **productsBindingSource**.  
  
7.  Haga clic en el botón situado a la derecha de la propiedad **DisplayMember** y seleccione **ProductName**.  
  
8.  Expanda la propiedad **DataBindings**, haga clic en el botón situado a la derecha de la propiedad **SelectedValue** y seleccione **Ninguno**.  
  
## Agregar un método para insertar datos en una tabla  
 La siguiente tarea consiste en leer los datos de los controles enlazados y en rellenar una tabla en el documento de Word.  En primer lugar, cree un procedimiento para dar formato a los encabezados de la tabla y, a continuación, agregue el método `AddData` para crear y dar formato a una tabla de Word.  
  
#### Para dar formato a los encabezados de la tabla  
  
1.  En la clase `ActionsControl`, cree un método para dar formato a los encabezados de la tabla.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#2)]
     [!code-vb[Trin_VstcoreActionsPaneWord#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#2)]  
  
#### Para crear la tabla  
  
1.  En la clase `ActionsControl`, escriba un método para crear una tabla si todavía no existe ninguno y agregue los datos del panel de acciones a la tabla.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#3)]
     [!code-vb[Trin_VstcoreActionsPaneWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#3)]  
  
#### Para insertar texto en una tabla de Word  
  
1.  Agregue el siguiente código al controlador de eventos <xref:System.Windows.Forms.Control.Click> del botón **Insert**.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#4)]
     [!code-vb[Trin_VstcoreActionsPaneWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ActionsControl.vb#4)]  
  
2.  En C\#, debe crear un controlador de eventos para el evento <xref:System.Windows.Forms.Control.Click> del botón.  Puede colocar este código en el controlador de eventos <xref:System.Windows.Forms.UserControl.Load> de la clase `ActionsControl`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ActionsControl.cs#5)]  
  
## Mostrar el panel de acciones  
 El panel de acciones se hace visible tras agregarle los controles.  
  
#### Para mostrar el panel de acciones  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en **ThisDocument.vb** o **ThisDocument.cs** y, a continuación, haga clic en **Ver código** en el menú contextual.  
  
2.  Cree una nueva instancia del control en la parte superior de la clase `ThisDocument` de modo que tenga un aspecto similar al del ejemplo siguiente.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreActionsPaneWord#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#6)]  
  
3.  Agregue código al controlador de eventos <xref:Microsoft.Office.Tools.Word.Document.Startup> de `ThisDocument` de modo que tenga un aspecto similar al del ejemplo siguiente.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreActionsPaneWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreActionsPaneWord/VB/ThisDocument.vb#7)]  
  
## Probar la aplicación  
 Ahora puede probar su documento para comprobar que el panel de acciones aparece cuando se abre el documento.  Pruebe la relación principal\-detalle en los controles del panel de acciones y asegúrese de que, al hacer clic en el botón **Insertar**, se rellenan los datos de una tabla de Word.  
  
#### Para probar el documento  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Confirme que el panel de acciones está visible.  
  
3.  Seleccione una compañía en el cuadro combinado y compruebe que cambian los elementos del cuadro de lista **Products**.  
  
4.  Seleccione un producto, haga clic en **Insertar** en el panel de acciones y compruebe que los detalles del producto se agregan a la tabla de Word.  
  
5.  Inserte otros productos de las distintas compañías.  
  
## Pasos siguientes  
 En este tutorial se muestran los aspectos básicos del enlace de datos a los controles de un panel de acciones en Word.  Éstas son algunas de las tareas que pueden venir a continuación:  
  
-   Enlazar datos a controles de Excel.  Para obtener más información, vea [Tutorial: Enlazar datos a controles en un panel de acciones de Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md).  
  
-   Implementar el proyecto.  Para obtener más información, vea [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Vea también  
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  