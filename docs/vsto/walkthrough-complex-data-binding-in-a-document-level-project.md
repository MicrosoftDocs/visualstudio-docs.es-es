---
title: "Tutorial: Enlace de datos complejo en un proyecto en el nivel del documento | Microsoft Docs"
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
  - "datos complejos [desarrollo de Office en Visual Studio]"
  - "datos [desarrollo de Office en Visual Studio], enlazar datos"
  - "enlace de datos [desarrollo de Office en Visual Studio], varias columnas"
  - "enlace de datos de varias columnas [desarrollo de Office en Visual Studio]"
ms.assetid: 32ffad3d-fba4-476a-99b8-ef440434f4e1
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# Tutorial: Enlace de datos complejo en un proyecto en el nivel del documento
  En este tutorial se muestran los fundamentos del enlace de datos complejos en un proyecto en el nivel del documento.  Puede enlazar varias celdas de una hoja de cálculo de Microsoft Office Excel a los campos de la base de datos Northwind de SQL Server.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar un origen de datos al proyecto de libro.  
  
-   Agregar controles enlazados a datos a una hoja de cálculo.  
  
-   Guardar en la base de datos los cambios realizados en los datos.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acceso a un servidor con la base de datos de ejemplo Northwind de SQL Server.  
  
-   Permisos de lectura y escritura en la base de datos de SQL Server.  
  
## Crear un proyecto nuevo  
 El primer paso es crear un proyecto de libro de Excel.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de libro de Excel con el nombre **Mi enlace de datos complejo**.  En el asistente, seleccione **Crear un nuevo documento**.  
  
     Para obtener más información, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el nuevo libro de Excel en el diseñador y agrega el proyecto **Mi enlace de datos complejo** al Explorador de soluciones.  
  
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
  
8.  Active la casilla que aparece junto a la tabla **Empleados**.  
  
9. Haga clic en **Finalizar**.  
  
 El asistente agrega la tabla **Empleados** a la ventana **Orígenes de datos**.  También agrega al proyecto un conjunto de datos con tipo, visible en el **Explorador de soluciones**.  
  
## Agregar controles a la hoja de cálculo  
 Una hoja de cálculo mostrará la tabla **Employees** cuando se abra el libro.  Los usuarios podrán realizar cambios en los datos y, a continuación, guardar estos cambios en la base de datos haciendo clic en un botón.  
  
 Para enlazar automáticamente la hoja de cálculo a la tabla, puede agregar un control <xref:Microsoft.Office.Tools.Excel.ListObject> a la hoja de cálculo desde la ventana **Orígenes de datos**.  Para dar al usuario la opción de guardar los cambios, agregue un control <xref:System.Windows.Forms.Button> desde el **Cuadro de herramientas**.  
  
#### Para agregar un objeto de lista  
  
1.  Compruebe que el libro **Mis datos complejos Binding.xlsx** está abierto en el diseñador de Visual Studio, con **Hoja1** mostrados.  
  
2.  Abra la ventana **Orígenes de datos** y seleccione el nodo **Empleados**.  
  
3.  Haga clic en la flecha de la lista desplegable que aparece.  
  
4.  Seleccione **ListObject** en la lista desplegable.  
  
5.  Arrastre la tabla **Employees** a la celda **A6**.  
  
     En la celda **A6** se crea un control <xref:Microsoft.Office.Tools.Excel.ListObject> llamado `EmployeesListObject`.  Al mismo tiempo, se agregan al proyecto un control <xref:System.Windows.Forms.BindingSource> denominado `EmployeesBindingSource`, un adaptador de tablas y una instancia de la clase <xref:System.Data.DataSet>.  El control se enlaza a <xref:System.Windows.Forms.BindingSource>, que, a su vez, se enlaza a la instancia de <xref:System.Data.DataSet>.  
  
#### Para agregar un botón  
  
1.  Desde la ficha **Controles comunes** del **Cuadro de herramientas**, agregue un control <xref:System.Windows.Forms.Button> a la celda **A4** de la hoja de cálculo.  
  
 El paso siguiente es agregar texto al botón cuando se abre la hoja de cálculo.  
  
## Inicializar el control  
 Agregue el texto al botón en el controlador de eventos <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>.  
  
#### Para inicializar el control  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en **Sheet1.vb** o **Sheet1.cs** y, a continuación, haga clic en **Ver código** en el menú contextual.  
  
2.  Agregue el código siguiente al método `Sheet1_Startup` para establecer el texto del b`utton`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#8)]
     [!code-vb[Trin_VstcoreDataExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#8)]  
  
3.  Sólo para C\#, agregue un controlador de eventos para el evento <xref:System.Windows.Forms.Control.Click> al método `Sheet1_Startup`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#9)]  
  
 Ahora agregue código para controlar el evento <xref:System.Windows.Forms.Control.Click> del botón.  
  
## Guardar los cambios en la base de datos  
 Cualquier cambio que se haya realizado en los datos sólo existe en el conjunto de datos local hasta que se guardan explícitamente en la base de datos.  
  
#### Para guardar los cambios en la base de datos  
  
1.  Agregue un controlador de eventos para el evento <xref:System.Windows.Forms.Control.Click> del b`utton` y agregue el código siguiente para confirmar todos los cambios realizados en el conjunto de datos y guardarlos en la base de datos.  
  
     [!code-csharp[Trin_VstcoreDataExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet3.vb#10)]  
  
## Probar la aplicación  
 Ahora puede probar el libro para comprobar de que los datos aparecen como se espera y que puede manipular los datos del objeto de lista.  
  
#### Para probar el enlace de datos  
  
-   Presione F5.  
  
     Compruebe que, cuando se abre el libro, el objeto de lista se rellena con los datos de la tabla **Empleados**.  
  
#### Para modificar los datos  
  
1.  Haga clic en la celda **B7**, que debe contener el apellido **Davolio**.  
  
2.  Escriba el apellido Anderson y, a continuación, presione ENTRAR.  
  
#### Para modificar un encabezado de columna  
  
1.  Haga clic en la celda que contiene el encabezado de columna **Apellidos**.  
  
2.  Escriba Apellidos y, a continuación, presione ENTRAR.  
  
#### Para guardar los datos  
  
1.  En la hoja de cálculo, haga clic en **Guardar**.  
  
2.  Salga de Excel.  Haga clic en **No** cuando se le pregunte si desea guardar los cambios realizados.  
  
3.  Presione F5 para ejecutar de nuevo el proyecto.  
  
     El objeto de lista se rellena con los datos de la tabla **Empleados**.  
  
4.  Observe que el apellido en la celda **B7** todavía es Anderson, que es el cambio que realizó en los datos y guardó en la base de datos.  El encabezado de columna **Apellidos** del encabezado de columna se ha vuelto a establecer en su formato original sin el espacio, porque el encabezado de columna no está enlazado a la base de datos y no guardó los cambios realizados en la hoja de cálculo.  
  
#### Para agregar nuevas filas  
  
1.  Seleccione una celda dentro del objeto de lista.  
  
     En la parte inferior de la lista aparece una nueva fila, con un asterisco \(**\***\) en la primera celda de la nueva fila.  
  
2.  Agregue la información siguiente en la fila vacía.  
  
    |IdEmpleado|Apellido|Nombre|Título|  
    |----------------|--------------|------------|------------|  
    |10|Ito|Shu|Director de ventas|  
  
#### Para eliminar filas  
  
-   Haga clic con el botón secundario en el número 16 \(fila 16\) en el extremo izquierdo de la hoja de cálculo y, a continuación, haga clic en **Eliminar**.  
  
#### Para ordenar las filas de la lista  
  
1.  Seleccione una celda dentro de la lista.  
  
     En cada encabezado de columna aparecen botones con flechas.  
  
2.  Haga clic en el botón de flecha del encabezado de columna **Apellidos**.  
  
3.  Haga clic en **Orden ascendente**.  
  
     Las filas se ordenan alfabéticamente en función de los apellidos.  
  
#### Para filtrar información  
  
1.  Seleccione una celda dentro de la lista.  
  
2.  Haga clic en el botón de flecha en el encabezado de columna **Cargo**.  
  
3.  Haga clic en **Representante de ventas**.  
  
     La lista muestra sólo las filas que tienen **Representante de ventas** en la columna **Cargo**.  
  
4.  Vuelva a hacer clic en el botón de flecha del encabezado de columna **Cargo**.  
  
5.  Haga clic en **\(Todos\)**.  
  
     Se quita la función de filtro y aparecen todas las filas.  
  
## Pasos siguientes  
 Este tutorial muestra los fundamentos para enlazar una tabla de una base de datos a un objeto de lista.  Éstas son algunas de las tareas que pueden venir a continuación:  
  
-   Almacene en memoria caché los datos para poder utilizarlos sin conexión.  Para obtener más información, vea [Cómo: Almacenar datos en la memoria caché para el uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Implementar la solución.  Para obtener más información, vea [Implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
-   Crear una relación de principal\-detalle entre un campo y una tabla.  Para obtener más información, vea [Tutorial: Crear una relación principal-detalle utilizando un conjunto de datos almacenado en caché](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).  
  
## Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Datos en las soluciones de Office](../vsto/data-in-office-solutions.md)   
 [Tutorial: Enlace de datos simple en un proyecto en el nivel del documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)  
  
  