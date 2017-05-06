---
title: "Tutorial: Crear una relaci&#243;n principal-detalle utilizando un conjunto de datos almacenado en cach&#233;"
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
  - "almacenamiento de datos en caché [desarrollo de Office en Visual Studio], Relación principal-detalle"
  - "tablas principal-detalle [desarrollo de Office en Visual Studio], tutoriales"
ms.assetid: 419f4e07-c67f-4fc9-973a-bc794f349ac3
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Tutorial: Crear una relaci&#243;n principal-detalle utilizando un conjunto de datos almacenado en cach&#233;
  En este tutorial se muestra cómo crear una relación principal\-detalle en una hoja de cálculo, así como a almacenar en memoria caché los datos para que la solución se pueda utilizar sin conexión.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Durante este tutorial aprenderá a:  
  
-   Agregar controles a una hoja de cálculo.  
  
-   Configurar un conjunto de datos para almacenarlo en memoria caché en una hoja de cálculo.  
  
-   Agregar código para habilitar el desplazamiento por los registros.  
  
-   Probar el proyecto.  
  
> [!NOTE]  
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté usando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acceso a la base de datos de ejemplo Northwind de SQL Server.  La base de datos puede estar en un equipo de desarrollo o en un servidor.  
  
-   Permisos de lectura y escritura en la base de datos de SQL Server.  
  
## Crear un proyecto nuevo  
 En este paso, creará un proyecto de libro de Excel.  
  
#### Para crear un nuevo proyecto  
  
1.  Con Visual Basic o C\#, cree un proyecto de libro de Excel con el nombre **Mi principal\-detalle**.  Asegúrese de que esté seleccionada la opción **Crear un nuevo documento**.  Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto Mi principal\-detalle al **Explorador de soluciones**.  
  
## Crear el origen de datos  
 Utilice la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.  
  
#### Para crear el origen de datos  
  
1.  Si la ventana **orígenes de datos** no está visible, muéstrela por, en la barra de menús, eligiendo **Vista**, **Otras ventanas**, **orígenes de datos**.  
  
2.  Elija **Agregar nuevo origen de datos** para iniciar **Asistente para la configuración de orígenes de datos**.  
  
3.  Seleccione **Base de datos** y, a continuación, haga clic en **Siguiente**.  
  
4.  Seleccione una conexión de datos a la base de datos de ejemplo Northwind de SQL Server o agregue una nueva conexión mediante el botón **Nueva conexión**.  
  
5.  Cuando haya seleccionado o creado una conexión, haga clic en **Siguiente**.  
  
6.  Si estuviera activada, desactive la opción de guardar la conexión y, a continuación, haga clic en **Siguiente**.  
  
7.  Expanda el nodo **Tablas** en la ventana **Objetos de base de datos**.  
  
8.  Seleccione la tabla **Orders** y la tabla **Order Details**.  
  
9. Haga clic en **Finalizar**.  
  
 El asistente agrega las dos tablas a la ventana **Data Sources**.  También agrega al proyecto un conjunto de datos con tipo, visible en el **Explorador de soluciones**.  
  
## Agregar controles a la hoja de cálculo  
 En este paso, agregará un rango con nombre, un objeto de lista y dos botones a la primera hoja de cálculo.  Primero, agregue el rango con nombre y el objeto de lista desde la ventana **Orígenes de datos** para que se enlacen automáticamente al origen de datos.  A continuación, agregue los botones del **Cuadro de herramientas**.  
  
#### Para agregar un rango con nombre y un objeto de lista  
  
1.  Compruebe que el libro **Mi Master\-Detail.xlsx** está abierto en el diseñador de Visual Studio, con **Hoja1** mostrados.  
  
2.  Abra la ventana **Data Sources** y expanda el nodo de **Orders**.  
  
3.  Seleccione la columna **OrderID** y, a continuación, haga clic en la flecha de lista desplegable que aparece.  
  
4.  Haga clic en **NamedRange** en la lista desplegable y, a continuación, arrastre la columna **OrderID** hasta la celda **A2**.  
  
     En la celda **A2** se crea un control <xref:Microsoft.Office.Tools.Excel.NamedRange> denominado `OrderIDNamedRange`.  Al mismo tiempo, se agregan al proyecto un control <xref:System.Windows.Forms.BindingSource> denominado `OrdersBindingSource`, un adaptador de tablas y una instancia de la clase <xref:System.Data.DataSet>.  El control se enlaza a <xref:System.Windows.Forms.BindingSource>, que, a su vez, se enlaza a la instancia de <xref:System.Data.DataSet>.  
  
5.  Desplácese hacia abajo, más allá de las columnas situadas bajo la tabla **Orders**.  En la parte inferior de la lista se encuentra la tabla **Order Details**; está aquí porque es un elemento secundario de la tabla **Orders**.  Seleccione esta tabla de **Order Details**, no la que está en el mismo nivel que la tabla de **Orders**; a continuación, haga clic en la flecha de lista desplegable que aparece.  
  
6.  Haga clic en **ListObject** en la lista desplegable y, a continuación, arrastre la tabla **OrderDetails** hasta la celda **A6**.  
  
7.  Se crea un control <xref:Microsoft.Office.Tools.Excel.ListObject> denominado **Order\_DetailsListObject** en la celda **A6** y se enlaza al objeto <xref:System.Windows.Forms.BindingSource>.  
  
#### Para agregar dos botones  
  
1.  Desde la ficha **Controles comunes** del **Cuadro de herramientas**, agregue un control <xref:System.Windows.Forms.Button> a la celda **A3** de la hoja de cálculo.  
  
     Este botón se denominará `Button1`.  
  
2.  Agregue otro control <xref:System.Windows.Forms.Button> a la celda **B3** de la hoja de cálculo.  
  
     Este botón se denominará `Button2`.  
  
 Luego, marque el conjunto de datos que se va a almacenar en memoria caché en el documento.  
  
## Almacenar en caché el conjunto de datos  
 Para marcar el conjunto de datos que se va a almacenar en memoria caché en el documento, haga público el conjunto de datos y establezca la propiedad **CacheInDocument**.  
  
#### Para almacenar en caché el conjunto de datos  
  
1.  Seleccione **NorthwindDataSet** en la bandeja de componentes.  
  
2.  En la Ventana **Propiedades**, cambie la propiedad **Modifiers** a **Pública**.  
  
     Los conjuntos de datos deben ser públicos antes de que se habilite el almacenamiento en memoria caché.  
  
3.  Cambie la propiedad **CacheInDocument** a **True**.  
  
 El siguiente paso consiste en agregar texto a los botones y, en C\#, agregar código para enlazar los controladores de eventos.  
  
## Inicializar los controles  
 Establezca el texto del botón y agregue controladores de eventos durante el evento <xref:Microsoft.Office.Tools.Excel.Workbook.Startup>.  
  
#### Para inicializar los datos y los controles  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en **Sheet1.vb** o **Sheet1.cs** y, a continuación, haga clic en **Ver código** en el menú contextual.  
  
2.  Agregue el código siguiente al método `Sheet1_Startup` para establecer el texto de los botones.  
  
     [!code-csharp[Trin_VstcoreDataExcel#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#15)]
     [!code-vb[Trin_VstcoreDataExcel#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#15)]  
  
3.  En C\# únicamente, agregue controladores de eventos para los eventos Click de los botones al método `Sheet1_Startup`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#16)]  
  
## Agregar código para habilitar el desplazamiento por los registros  
 Agregue el código al controlador del evento <xref:System.Windows.Forms.Control.Click> de cada botón para desplazarse por los registros.  
  
#### Para desplazarse por los registros  
  
1.  Agregue un controlador de eventos para el evento <xref:System.Windows.Forms.Control.Click> de `Button1` y agregue el código siguiente para retroceder por los registros:  
  
     [!code-csharp[Trin_VstcoreDataExcel#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#17)]
     [!code-vb[Trin_VstcoreDataExcel#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#17)]  
  
2.  Agregue un controlador de eventos para el evento <xref:System.Windows.Forms.Control.Click> de `Button2` y agregue el código siguiente para avanzar por los registros:  
  
     [!code-csharp[Trin_VstcoreDataExcel#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet2.cs#18)]
     [!code-vb[Trin_VstcoreDataExcel#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet2.vb#18)]  
  
## Probar la aplicación  
 Ahora puede probar el libro para asegurarse de que los datos aparecen según lo previsto y que puede utilizar la solución sin conexión.  
  
#### Para probar el almacenamiento de datos en caché  
  
1.  Presione **F5**.  
  
2.  Compruebe que el rango con nombre y el objeto de lista se han rellenado con datos del origen de datos.  
  
3.  Desplácese por algunos de los registros haciendo clic en los botones.  
  
4.  Guarde el libro y, a continuación, cierre el libro y Visual Studio.  
  
5.  Deshabilite la conexión a la base de datos.  Desconecte el cable de red del equipo si la base de datos está en un servidor, o detenga el servicio de SQL Server si la base de datos está en el equipo de desarrollo.  
  
6.  Excel abra y, a continuación **Mi Master\-Detail.xlsx** abierto de \\bin \\bin directory \(\\My Master\-Detail\\bin in Visual Basic or \\My Master\-Detail\\bin\\debug in C \(\\my master\-detail\\bin \\bin directory \(\\My Master\-Detail\\bin in Visual Basic or \\My Master\-Detail\\bin\\debug in C \\bin directory \(\\My Master\-Detail\\bin in Visual Basic or \\My Master\-Detail\\bin\\debug in C \\bin directory \(\\My Master\-Detail\\bin in Visual Basic or \\My Master\-Detail\\bin\\debug in C \\bin directory \(\\My Master\-Detail\\bin in Visual Basic or \\My Master\-Detail\\bin\\debug in C \\my master\-detail\\bin\\debug \\bin directory \(\\My Master\-Detail\\bin in Visual Basic or \\My Master\-Detail\\bin\\debug in C c\#\).  
  
7.  Desplácese por algunos de los registros para comprobar que la hoja de cálculo funciona normalmente cuando se está sin conexión.  
  
8.  Restablezca la conexión a la base de datos.  Vuelva a conectar el equipo a la red si la base de datos está en un servidor, o inicie el servicio de SQL Server si la base de datos está en el equipo de desarrollo.  
  
## Pasos siguientes  
 En este tutorial se muestran los fundamentos de la creación de una relación de datos principal\-detalle en una hoja de cálculo y del almacenamiento en memoria caché de un conjunto de datos.  Éstas son algunas de las tareas que pueden venir a continuación:  
  
-   Implementar la solución.  Para obtener más información, consulte [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
  
## Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Datos en las soluciones de Office](../vsto/data-in-office-solutions.md)   
 [Almacenar datos en caché](../vsto/caching-data.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
  