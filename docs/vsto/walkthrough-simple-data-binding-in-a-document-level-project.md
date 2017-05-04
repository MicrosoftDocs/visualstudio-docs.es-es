---
title: "Tutorial: Enlace de datos simple en un proyecto en el nivel del documento | Microsoft Docs"
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
  - "datos [desarrollo de Office en Visual Studio], enlazar datos"
  - "enlace de datos [desarrollo de Office en Visual Studio], celda de una hoja de cálculo a un campo de una base de datos"
  - "campo de base de datos [desarrollo de Office en Visual Studio]"
  - "enlace de datos simple [desarrollo de Office en Visual Studio]"
  - "hojas de cálculo [desarrollo de Office en Visual Studio], enlazar celda de una hoja de cálculo a un campo de una base de datos"
ms.assetid: 6b8fd638-af13-4ea1-b1c0-2763e2d8ae23
caps.latest.revision: 58
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 57
---
# Tutorial: Enlace de datos simple en un proyecto en el nivel del documento
  En este tutorial se muestran los fundamentos de enlace de datos en un proyecto en el nivel del documento.  Un único campo de datos de una base de datos de SQL Server se enlaza a un rango con nombre en Microsoft Office Excel.  En el tutorial también se muestra cómo agregar controles que permiten desplazarse por todos los registros de la tabla.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Crear un origen de datos para un proyecto de Excel.  
  
-   Agregar controles a una hoja de cálculo.  
  
-   Desplazarse por los registros de una bases de datos.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acceso a un servidor con la base de datos de ejemplo Northwind de SQL Server.  
  
-   Permisos de lectura y escritura en la base de datos de SQL Server.  
  
## Crear un proyecto nuevo  
 En este paso, creará un proyecto de libro de Excel.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre **My Simple Data Binding** mediante Visual Basic o C\#.  Asegúrese de que esté seleccionada la opción **Crear un nuevo documento**.  Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto My Simple Data Binding al **Explorador de soluciones**.  
  
## Crear el origen de datos  
 Utilice la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.  
  
#### Para crear el origen de datos  
  
1.  Si la ventana **orígenes de datos** no está visible, muéstrela por, en la barra de menús, eligiendo **Vista**, **Otras ventanas**, **orígenes de datos**.  
  
2.  Elija **Agregar nuevo origen de datos** para iniciar **Asistente para la configuración de orígenes de datos**.  
  
3.  Seleccione **Base de datos** y, a continuación, haga clic en **Siguiente**.  
  
4.  Seleccione una conexión de datos con la base de datos de ejemplo Northwind de SQL Server o agregue una nueva conexión mediante el botón **Nueva conexión**.  
  
5.  Cuando haya seleccionado o creado una conexión, haga clic en **Siguiente**.  
  
6.  Si estuviera activada, desactive la opción de guardar la conexión y, a continuación, haga clic en **Siguiente**.  
  
7.  Expanda el nodo **Tablas** en la ventana **Objetos de base de datos**.  
  
8.  Active la casilla que se encuentra junto a la tabla **Customers**.  
  
9. Haga clic en **Finalizar**.  
  
 El asistente agrega la tabla **Customers** a la ventana **Orígenes de datos**.  También agrega al proyecto un conjunto de datos con tipo, visible en el **Explorador de soluciones**.  
  
## Agregar controles a la hoja de cálculo  
 Para este tutorial, necesita dos rangos con nombre y cuatro botones en la primera hoja de cálculo.  En primer lugar, agregue los dos rangos con nombre de la ventana **Orígenes de datos** para que se enlacen al origen de datos de forma automática.  A continuación, agregue los botones del **Cuadro de herramientas**.  
  
#### Para agregar dos rangos con nombre  
  
1.  Compruebe que el libro **Mis datos simples Binding.xlsx** está abierto en el diseñador de Visual Studio, con **Hoja1** mostrados.  
  
2.  Abra la ventana **Orígenes de datos** y expanda el nodo **Customers**.  
  
3.  Seleccione la columna **CompanyName** y, a continuación, haga clic en la flecha de lista desplegable que aparece.  
  
4.  Seleccione **NamedRange** en la lista desplegable y, a continuación, arrastre la columna **CompanyName** hacia la celda **A1**.  
  
     En la celda **A1** se crea un control <xref:Microsoft.Office.Tools.Excel.NamedRange> denominado `companyNameNamedRange`.  Al mismo tiempo, se agregan al proyecto un control <xref:System.Windows.Forms.BindingSource> denominado `customersBindingSource`, un adaptador de tablas y una instancia de la clase <xref:System.Data.DataSet>.  El control se enlaza a <xref:System.Windows.Forms.BindingSource>, que, a su vez, se enlaza a la instancia de <xref:System.Data.DataSet>.  
  
5.  Seleccione la columna **CustomerID** en la ventana **Orígenes de datos** y, a continuación, haga clic en la flecha de lista desplegable que aparece.  
  
6.  Seleccione **NamedRange** en la lista desplegable y, a continuación, arrastre la columna **CustomerID** a la celda **B1**.  
  
7.  En la celda **B1** se crea otro control <xref:Microsoft.Office.Tools.Excel.NamedRange> denominado `customerIDNamedRange` y se enlaza al control <xref:System.Windows.Forms.BindingSource>.  
  
#### Para agregar cuatro botones  
  
1.  Desde la ficha **Controles comunes** del **Cuadro de herramientas**, agregue un control <xref:System.Windows.Forms.Button> a la celda **A3** de la hoja de cálculo.  
  
     Este botón se denominará `Button1`.  
  
2.  Agregue tres botones más a las celdas siguientes en el orden que se indica para que los nombres sean los que se muestran a continuación:  
  
    |Celda|\(Nombre\)|  
    |-----------|----------------|  
    |B3|Button2|  
    |C3|Button3|  
    |D3|Button4|  
  
 El paso siguiente consiste en agregar texto a los botones y en agregar controladores de eventos en C\#.  
  
## Inicializar los controles  
 Establezca el texto del botón y agregue controladores de eventos durante el evento <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>.  
  
#### Para inicializar los controles  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en **Sheet1.vb** o **Sheet1.cs** y, a continuación, haga clic en **Ver código** en el menú contextual.  
  
2.  Agregue el código siguiente al método `Sheet1_Startup` para establecer el texto de cada botón.  
  
     [!code-csharp[Trin_VstcoreDataExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreDataExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#2)]  
  
3.  En C\# únicamente, agregue controladores de eventos para los eventos Click de los botones al método `Sheet1_Startup`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#3)]  
  
 Ahora agregue el código para controlar los eventos <xref:System.Windows.Forms.Control.Click> de los botones de forma que el usuario pueda desplazarse por los registros.  
  
## Agregar código para habilitar el desplazamiento por los registros  
 Agregue el código al controlador del evento <xref:System.Windows.Forms.Control.Click> de cada botón para desplazarse por los registros.  
  
#### Para desplazarse al primer registro  
  
1.  Agregue un controlador de eventos para el evento <xref:System.Windows.Forms.Control.Click> del botón `Button1` y agregue el código siguiente para desplazarse al primer registro:  
  
     [!code-csharp[Trin_VstcoreDataExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreDataExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#4)]  
  
#### Para desplazarse al registro anterior  
  
1.  Agregue un controlador de eventos para el evento <xref:System.Windows.Forms.Control.Click> del botón `Button2` y agregue el código siguiente para retroceder una posición:  
  
     [!code-csharp[Trin_VstcoreDataExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreDataExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#5)]  
  
#### Para desplazarse al registro siguiente  
  
1.  Agregue un controlador de eventos para el evento <xref:System.Windows.Forms.Control.Click> del botón `Button3` y agregue el código siguiente para avanzar una posición:  
  
     [!code-csharp[Trin_VstcoreDataExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreDataExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#6)]  
  
#### Para desplazarse al último registro  
  
1.  Agregue un controlador de eventos para el evento <xref:System.Windows.Forms.Control.Click> del botón `Button4` y agregue el código siguiente para desplazarse al último registro:  
  
     [!code-csharp[Trin_VstcoreDataExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreDataExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#7)]  
  
## Probar la aplicación  
 Ahora puede probar el libro para asegurarse de que puede desplazarse por los registros de la base de datos.  
  
#### Para probar el libro  
  
1.  Presione F5 para ejecutar el proyecto.  
  
2.  Confirme que el primer registro aparece en las celdas **A1** y **B1**.  
  
3.  Haga clic en el botón **\>** \(`Button3`\) y confirme que el registro siguiente aparece en las celdas **A1** y **B1**.  
  
4.  Haga clic en los otros botones de desplazamiento para confirmar que el registro cambia tal y como se espera.  
  
## Pasos siguientes  
 En este tutorial se muestran los aspectos básicos del enlace de un rango con nombre a un campo de una base de datos.  Éstas son algunas de las tareas que pueden venir a continuación:  
  
-   Almacene en memoria caché los datos para poder utilizarlos sin conexión.  Para obtener más información, vea [Cómo: Almacenar datos en la memoria caché para el uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Enlazar celdas a varias columnas de una tabla, en lugar de a un campo.  Para obtener más información, vea [Tutorial: Enlace de datos complejo en un proyecto en el nivel del documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md).  
  
-   Utilizar un control <xref:System.Windows.Forms.BindingNavigator> para desplazarse por los registros.  Para obtener más información, vea [Cómo: Explorar datos con el control BindingNavigator de formularios Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb).  
  
## Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Datos en las soluciones de Office](../vsto/data-in-office-solutions.md)   
 [Tutorial: Enlace de datos complejo en un proyecto en el nivel del documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)  
  
  