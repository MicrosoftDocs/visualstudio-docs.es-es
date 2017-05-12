---
title: "Tutorial: enlace de datos complejos en un proyecto de complemento de VSTO"
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
  - "datos [desarrollo de Office en Visual Studio], enlace de datos"
  - "enlace de datos [desarrollo de Office en Visual Studio], Word"
  - "datos [desarrollo de Office en Visual Studio], enlace de datos simple"
ms.assetid: b248d194-a8b1-4f87-94c4-24e940eea1fd
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Tutorial: enlace de datos complejos en un proyecto de complemento de VSTO
  Puede enlazar datos a controles host y controles de Windows Forms en proyectos de complemento de VSTO. En este tutorial se muestra cómo se agregan controles a un documento de Microsoft Office Word y cómo se enlazan los controles a datos en tiempo de ejecución.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Agregar un elemento <xref:Microsoft.Office.Tools.Word.ContentControl> a un documento en tiempo de ejecución.  
  
-   Crear un elemento <xref:System.Windows.Forms.BindingSource> que conecta el control a una instancia de un conjunto de datos.  
  
-   Permitir al usuario que se desplace por los registros y visualizarlos en el control.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
-   Acceso a una instancia en ejecución de SQL Server 2005 o SQL Server 2005 Express que tenga asociada la base de datos de ejemplo `AdventureWorksLT`. La base de datos `AdventureWorksLT` se puede descargar del [sitio web de CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Para obtener más información sobre cómo asociar una base de datos, vea los siguientes temas:  
  
    -   Para asociar una base de datos mediante SQL Server Management Studio o SQL Server Management Studio Express, vea [Cómo: asociar una base de datos \(SQL Server Management Studio\)](http://msdn.microsoft.com/es-es/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Para asociar una base de datos mediante la línea de comandos, vea [Cómo: asociar un archivo de base de datos a SQL Server Express](http://msdn.microsoft.com/es-es/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Crear un proyecto nuevo  
 El primer paso es crear un proyecto de complemento de VSTO de Word.  
  
#### Para crear un nuevo proyecto  
  
1.  Cree un proyecto de complemento de VSTO para Word con el nombre **Rellenar documentos desde una base de datos**, mediante Visual Basic o C\#.  
  
     Para obtener más información, consulta [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio abre el archivo ThisAddIn.vb o ThisAddIn.cs y agrega el proyecto **Rellenar documentos desde una base de datos** al **Explorador de soluciones**.  
  
2.  Si su proyecto tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], agregue una referencia al ensamblado Microsoft.Office.Tools.Word.v4.0.Utilities.dll. Esta referencia es obligatoria para agregar mediante programación controles de Windows Forms al documento más adelante en este tutorial.  
  
## Crear un origen de datos  
 Use la ventana **Orígenes de datos** para agregar un conjunto de datos con tipo al proyecto.  
  
#### Para agregar un conjunto de datos con tipo al proyecto  
  
1.  Si la ventana **Orígenes de datos** no es visible, muéstrela; para ello, en la barra de menús, elija **Ver**, **Otras ventanas**, **Orígenes de datos**.  
  
2.  Elija **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Haga clic en **Base de datos** y luego en **Siguiente**.  
  
4.  Si ya tiene una conexión a la base de datos `AdventureWorksLT`, elija esa conexión y haga clic en **Siguiente**.  
  
     De lo contrario, haga clic en **Nueva conexión** y use el cuadro de diálogo **Agregar conexión** para crear la nueva conexión. Para obtener más información, consulta [Cómo: Conectarse a los datos de una base de datos](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
5.  En la página **Guardar cadena de conexión en el archivo de configuración de la aplicación**, haga clic en **Siguiente**.  
  
6.  En la página **Elegir los objetos de base de datos** expanda **Tablas** y seleccione **Customer \(SalesLT\)**.  
  
7.  Haga clic en **Finalizar**.  
  
     El archivo AdventureWorksLTDataSet.xsd se agrega al **Explorador de soluciones**. Este archivo define los siguientes elementos:  
  
    -   Un conjunto de datos con tipo denominado `AdventureWorksLTDataSet`. Este conjunto de datos representa el contenido de la tabla **Customer \(SalesLT\)** de la base de datos AdventureWorksLT.  
  
    -   Un TableAdapter denominado `CustomerTableAdapter`. Este TableAdapter puede usarse para leer y escribir datos en `AdventureWorksLTDataSet`. Para obtener más información, consulta [Información general sobre TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
     Estos dos objetos se usarán más adelante en este tutorial.  
  
## Crear controles y enlazarlos a datos  
 La interfaz para ver registros de la base de datos en este tutorial es muy básica y se crea dentro del documento. Un elemento <xref:Microsoft.Office.Tools.Word.ContentControl> muestra un registro único de la base de datos a la vez y dos controles <xref:Microsoft.Office.Tools.Word.Controls.Button> le permiten desplazarse hacia delante y atrás por los registros. El control de contenido usa un elemento <xref:System.Windows.Forms.BindingSource> para conectarse a la base de datos.  
  
 Para más información sobre el enlace de controles a datos, consulte [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### Para crear la interfaz en el documento  
  
1.  En la clase `ThisAddIn`, declare los siguientes controles para mostrar y desplazarse por la tabla `Customer` de la base de datos `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_WordAddInDatabase#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDatabase#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#1)]  
  
2.  En el método `ThisAddIn_Startup`, agregue el siguiente código para inicializar el conjunto de datos y rellenarlo con la información de la base de datos `AdventureWorksLTDataSet`.  
  
     [!code-csharp[Trin_WordAddInDatabase#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDatabase#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#2)]  
  
3.  Agregue el código siguiente al método `ThisAddIn_Startup`. Esto genera un elemento host que extiende el documento. Para obtener más información, consulta [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
     [!code-csharp[Trin_WordAddInDatabase#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDatabase#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#3)]  
  
4.  Defina varios intervalos al principio del documento. Estos intervalos identifican dónde se insertará texto y se colocarán los controles.  
  
     [!code-csharp[Trin_WordAddInDatabase#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDatabase#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#4)]  
  
5.  Agregue los controles de interfaz a los intervalos definidos previamente.  
  
     [!code-csharp[Trin_WordAddInDatabase#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddInDatabase#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#5)]  
  
6.  Enlace el control de contenido a `AdventureWorksLTDataSet` mediante el elemento <xref:System.Windows.Forms.BindingSource>. Para los desarrolladores de C\#, agregue dos controladores de eventos para los controles <xref:Microsoft.Office.Tools.Word.Controls.Button>.  
  
     [!code-csharp[Trin_WordAddInDatabase#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddInDatabase#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#6)]  
  
7.  Agregue el código siguiente para navegar por los registros de la base de datos.  
  
     [!code-csharp[Trin_WordAddInDatabase#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDatabase#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDatabase/VB/ThisAddIn.vb#7)]  
  
## Probar el complemento  
 Cuando abre Word, el control de contenido muestra los datos del conjunto de datos `AdventureWorksLTDataSet`. Desplácese por los registros de la base de datos haciendo clic en los botones **Siguiente** y **Anterior**.  
  
#### Para probar el complemento de VSTO  
  
1.  Presione **F5**.  
  
     Se crea un control de contenido denominado `customerContentControl` y se rellena con datos. Al mismo tiempo, se agregan al proyecto un objeto de conjunto de datos denominado `adventureWorksLTDataSet` y un elemento <xref:System.Windows.Forms.BindingSource> con el nombre `customerBindingSource`. El elemento <xref:Microsoft.Office.Tools.Word.ContentControl> se enlaza al elemento <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza al objeto de conjunto de datos.  
  
2.  Haga clic en los botones **Siguiente** y **Anterior** para desplazarse por los registros de la base de datos.  
  
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
 [Cómo: Rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Cómo: Actualizar un origen de datos con datos de un control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Información general sobre el uso de archivos de bases de datos locales en soluciones de Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Conectar a los datos en aplicaciones de Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Información general sobre el componente BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  