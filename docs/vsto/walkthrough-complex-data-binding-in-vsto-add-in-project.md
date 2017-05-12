---
title: "Tutorial: enlace de datos complejos en el proyecto de complemento de VSTO"
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
  - "enlace de datos [desarrollo de Office en Visual Studio], Excel"
  - "datos [desarrollo de Office en Visual Studio], enlace de datos"
  - "datos complejos [desarrollo de Office en Visual Studio]"
ms.assetid: ff52fb56-1f67-4ae2-a3d1-93038619d4e6
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Tutorial: enlace de datos complejos en el proyecto de complemento de VSTO
  Puede enlazar datos a controles host y controles de Windows Forms en proyectos de complemento de VSTO. En este tutorial se muestra cómo agregar controles a una hoja de cálculo de Microsoft Office Excel y enlazar los controles a datos en tiempo de ejecución.  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar un control <xref:Microsoft.Office.Tools.Excel.ListObject> a una hoja de cálculo en tiempo de ejecución.  
  
-   Crear un <xref:System.Windows.Forms.BindingSource> que conecta el control a una instancia de un conjunto de datos.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acceso a una instancia en ejecución de SQL Server 2005 o SQL Server 2005 Express que tenga asociada la base de datos de ejemplo `AdventureWorksLT`. La base de datos `AdventureWorksLT` se puede descargar del [sitio web de CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Para obtener más información sobre cómo asociar una base de datos, vea los siguientes temas:  
  
    -   Para asociar una base de datos mediante SQL Server Management Studio o SQL Server Management Studio Express, vea [Cómo: asociar una base de datos \(SQL Server Management Studio\)](http://msdn.microsoft.com/es-es/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Para asociar una base de datos mediante la línea de comandos, vea [Cómo: asociar un archivo de base de datos a SQL Server Express](http://msdn.microsoft.com/es-es/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Crear un proyecto nuevo  
 En primer lugar, es necesario crear un proyecto de complemento de VSTO para Excel.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de complemento de VSTO para Excel con el nombre **Rellenar hojas de cálculo de una base de datos**, mediante Visual Basic o C\#.  
  
     Para obtener más información, consulta [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el archivo `ThisAddIn.vb` o `ThisAddIn.cs` y agrega el proyecto **Rellenar hojas de cálculo de una base de datos** al **Explorador de soluciones**.  
  
## Crear un origen de datos  
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.  
  
#### Para agregar un conjunto de datos con tipo al proyecto  
  
1.  Si la ventana **Orígenes de datos** no es visible, muéstrela; para ello, en la barra de menús, elija **Ver**, **Otras ventanas**, **Orígenes de datos**.  
  
2.  Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Haga clic en **Base de datos** y luego en **Siguiente**.  
  
4.  Si ya tiene una conexión a la base de datos `AdventureWorksLT`, elija esa conexión y haga clic en **Siguiente**.  
  
     De lo contrario, haga clic en **Nueva conexión** y use el cuadro de diálogo **Agregar conexión** para crear la nueva conexión. Para obtener más información, consulta [Cómo: Conectarse a los datos de una base de datos](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
5.  En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación**, haga clic en **Siguiente**.  
  
6.  En la página **Elegir los objetos de base de datos** expanda **Tablas** y seleccione **Dirección \(SalesLT\)**.  
  
7.  Haga clic en **Finalizar**.  
  
     El archivo AdventureWorksLTDataSet.xsd se agrega al **Explorador de soluciones**. Este archivo define los siguientes elementos:  
  
    -   Un conjunto de datos con tipo denominado `AdventureWorksLTDataSet`. Este conjunto de datos representa el contenido de la tabla **Dirección \(SalesLT\)** de la base de datos AdventureWorksLT.  
  
    -   Un TableAdapter denominado `AddressTableAdapter`. Este TableAdapter puede usarse para leer y escribir datos en `AdventureWorksLTDataSet`. Para obtener más información, consulta [Información general sobre TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
     Estos dos objetos se usarán más adelante en este tutorial.  
  
## Crear controles y enlazarlos a datos  
 En este tutorial, el control <xref:Microsoft.Office.Tools.Excel.ListObject> muestra todos los datos en la tabla seleccionada en cuanto el usuario abre el libro. El objeto de lista usa <xref:System.Windows.Forms.BindingSource> para conectar el control a la base de datos.  
  
 Para obtener más información sobre el enlace de controles, consulte [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### Para agregar el objeto de lista, el conjunto de datos y el adaptador de tabla  
  
1.  En la clase `ThisAddIn`, declare los siguientes controles para mostrar la tabla `Address` del conjunto de datos `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  En el método `ThisAddIn_Startup`, agregue el siguiente código para inicializar el conjunto de datos y rellenarlo con la información del conjunto de datos `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  Agregue el código siguiente al método `ThisAddIn_Startup`. Esto genera un elemento host que extiende la hoja de cálculo. Para obtener más información, consulta [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_ExcelAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  Cree un rango y agregue el control <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  Enlace el objeto de lista a `AdventureWorksLTDataSet` mediante <xref:System.Windows.Forms.BindingSource>. Pase los nombres de las columnas que desea enlazar al objeto de lista.  
  
     [!code-csharp[Trin_ExcelAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInDatabase/VB/ThisAddIn.vb#5)]  
  
## Probar el complemento  
 Al abrir Excel, el control <xref:Microsoft.Office.Tools.Excel.ListObject> muestra los datos de la tabla `Address` del conjunto de datos `AdventureWorksLTDataSet`.  
  
#### Para probar el complemento de VSTO  
  
-   Presione **F5**.  
  
     Se creará un control <xref:Microsoft.Office.Tools.Excel.ListObject> denominado `addressListObject` en la hoja de cálculo. Al mismo tiempo, se agregan al proyecto un objeto de conjunto de datos denominado `adventureWorksLTDataSet` y una <xref:System.Windows.Forms.BindingSource> denominada `addressBindingSource`. El <xref:Microsoft.Office.Tools.Excel.ListObject> se enlaza a <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza al objeto de conjunto de datos.  
  
## Vea también  
 [Datos en las soluciones de Office](../vsto/data-in-office-solutions.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Cómo: Rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Cómo: Rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Cómo: Rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Cómo: Rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Cómo: Desplazarse por los registros de una base de datos en una hoja de cálculo](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Cómo: Actualizar un origen de datos con datos de un control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Tutorial: Enlace de datos simple en un proyecto en el nivel del documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)   
 [Tutorial: Enlace de datos complejo en un proyecto en el nivel del documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)   
 [Información general sobre el uso de archivos de bases de datos locales en soluciones de Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Información general sobre el uso de archivos de bases de datos locales en soluciones de Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Conectar a los datos en aplicaciones de Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Información general sobre el componente BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  