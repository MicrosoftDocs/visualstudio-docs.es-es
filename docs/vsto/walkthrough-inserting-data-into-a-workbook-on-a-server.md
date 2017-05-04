---
title: "Tutorial: Insertar datos en un libro de trabajo de un servidor | Microsoft Docs"
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
  - "datos [desarrollo de Office en Visual Studio], acceso en el servidor"
  - "conjuntos de datos [desarrollo de Office en Visual Studio], acceso en el servidor"
  - "documentos [desarrollo de Office en Visual Studio], acceso a datos en el servidor"
  - "acceso a datos en el servidor [desarrollo de Office en Visual Studio]"
  - "libros [desarrollo de Office en Visual Studio], insertar datos"
ms.assetid: e6481902-781c-4666-bc18-4d69368c9bb3
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Tutorial: Insertar datos en un libro de trabajo de un servidor
  Este tutorial muestra cómo insertar datos en un conjunto de datos que está almacenado en memoria caché en un libro de Microsoft Office Excel sin iniciar Excel, mediante la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 En este tutorial se muestran las tareas siguientes:  
  
-   Definir un conjunto de datos que contenga datos de la base de datos AdventureWorksLT.  
  
-   Crear instancias del conjunto de datos en un proyecto de libro de Excel y un proyecto de aplicación de consola.  
  
-   Crear un objeto <xref:Microsoft.Office.Tools.Excel.ListObject> que se enlaza al conjunto de datos del libro.  
  
-   Agregar el conjunto de datos del libro a la memoria caché de datos.  
  
-   Insertar los datos en el conjunto de datos almacenado en memoria caché ejecutando el código en la aplicación de consola, sin iniciar Excel.  
  
 Si bien en este tutorial se supone que el código se ejecuta en un equipo de desarrollo, el código que se muestra en este tutorial puede utilizarse en un servidor que no tenga instalado Excel.  
  
> [!NOTE]  
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté usando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] o [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
-   Acceso a una instancia en ejecución de Microsoft SQL Server o Microsoft SQL Server Express que tenga adjunta la base de datos de ejemplo AdventureWorksLT.  La base de datos AdventureWorksLT se puede descargar desde el [sitio web de CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  Para obtener más información sobre cómo asociar una base de datos, vea los siguientes temas:  
  
    -   Para adjuntar una base de datos mediante SQL Server Management Studio o SQL Server Management Studio Express, vea [Cómo adjuntar una base de datos \(SQL Server Management Studio\)](http://msdn.microsoft.com/es-es/b4efb0ae-cfe6-4d81-a4b4-6e4916885caa).  
  
    -   Para adjuntar una base de datos mediante la línea de comandos, vea [Cómo adjuntar un archivo de base de datos a SQL Server Express](http://msdn.microsoft.com/es-es/0f8e42b5-7a8c-4c30-8c98-7d2bdc8dcc68).  
  
## Crear un proyecto de biblioteca de clases que defina un conjunto de datos  
 Para utilizar el mismo conjunto de datos en un libro de Excel y en una aplicación de consola, debe definirlo en un ensamblado independiente al que ambos proyectos hagan referencia.  Para este tutorial, defina el conjunto de datos en un proyecto de biblioteca de clases.  
  
#### Para crear el proyecto de bibliotecas de clases  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En el menú **Archivo**, elija **Nuevo** y haga clic en **Proyecto**.  
  
3.  En el panel de plantillas, expanda **Visual C\#** o **Visual Basic** y, a continuación, haga clic en **Windows**.  
  
4.  En la lista de plantillas de proyecto, seleccione **Biblioteca de clases**.  
  
5.  En el cuadro **Nombre**, escriba **AdventureWorksDataSet**.  
  
6.  Haga clic en **Examinar**, vaya a la carpeta %UserProfile%\\Mis documentos \(para Windows XP y versiones anteriores\) o la carpeta %UserProfile%\\Documentos \(para Windows Vista\) y, a continuación, haga clic en **Seleccionar carpeta**.  
  
7.  En el cuadro de diálogo **Nuevo proyecto**, asegúrese de que no esté activada la casilla **Crear directorio para la solución**.  
  
8.  Haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **AdventureWorksDataSet** al **Explorador de soluciones** y abre el archivo de código **Class1.cs** o **Class1.vb**.  
  
9. En el **Explorador de soluciones**, haga clic con el botón secundario en **Class1.cs** o **Class1.vb** y, a continuación, haga clic en **Eliminar**.  No necesita este archivo para este tutorial.  
  
## Definir un conjunto de datos en el proyecto de biblioteca de clases  
 Defina un conjunto de datos con tipo que contenga datos de la base de datos AdventureWorksLT para SQL Server 2005.  Más adelante en este tutorial, hará referencia a este conjunto de datos desde un proyecto de libro de Excel y un proyecto de aplicación de consola.  
  
 El conjunto de datos es un *conjunto de datos con tipo* que representa los datos de la tabla Product en la base de datos AdventureWorksLT.  Para obtener más información sobre los conjuntos de datos con tipo, vea [Trabajar con los conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
#### Para definir un conjunto de datos con tipo en el proyecto de biblioteca de clases  
  
1.  En el **Explorador de soluciones**, haga clic en el proyecto **AdventureWorksDataSet**.  
  
2.  Si la ventana **orígenes de datos** no está visible, muéstrela por, en la barra de menús, eligiendo **Vista**, **Otras ventanas**, **orígenes de datos**.  
  
3.  Elija **Agregar nuevo origen de datos** para iniciar **Asistente para la configuración de orígenes de datos**.  
  
4.  Haga clic en **Base de datos** y, a continuación, haga clic en **Siguiente**.  
  
5.  Si ya existe una conexión con la base de datos AdventureWorksLT, elija esta conexión y, a continuación, haga clic en **Siguiente**.  
  
     De lo contrario, haga clic en **Nueva conexión** y utilice el cuadro de diálogo **Agregar conexión** para crear la nueva conexión.  Para obtener más información, vea [How to: Connect to Data in a Database](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md).  
  
6.  En la página **Save the Connection String to the Application Configuration File**, haga clic en **Next**.  
  
7.  En la página **Elija los objetos de base de datos**, expanda **Tablas** y, a continuación, seleccione **Product \(SalesLT\)**.  
  
8.  Haga clic en **Finalizar**.  
  
     Se agrega el archivo AdventureWorksLTDataSet.xsd al proyecto **AdventureWorksDataSet**.  Este archivo define los siguientes elementos:  
  
    -   Un conjunto de datos con tipo denominado `AdventureWorksLTDataSet`.  Este conjunto de datos representa el contenido de la tabla Product en la base de datos AdventureWorksLT.  
  
    -   Objeto TableAdapter denominado `ProductTableAdapter`.  Este TableAdapter puede usarse para leer y escribir datos en `AdventureWorksLTDataSet`.  Para obtener más información, vea [Información general sobre TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
     Estos dos objetos se utilizarán más adelante en este tutorial.  
  
9. En el **Explorador de soluciones**, haga clic con el botón secundario en **AdventureWorksDataSet** y, a continuación, haga clic en **Compilar**.  
  
     Compruebe si el proyecto se compila sin errores.  
  
## Crear un proyecto de libro de Excel  
 Cree un proyecto de libro de Excel para la interfaz a los datos.  Más adelante en este tutorial, va a crear un control <xref:Microsoft.Office.Tools.Excel.ListObject> que muestre los datos y va a agregar una instancia del conjunto de datos a la memoria caché de datos del libro.  
  
#### Para crear un proyecto de libro de Excel  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en la solución **AdventureWorksDataSet**, elija **Agregar** y, a continuación, haga clic en **Nuevo proyecto**.  
  
2.  En el panel de plantillas, expanda **Visual c\#** o  **Visual Basic** y, a continuación **Office\/SharePoint**.  
  
3.  Bajo el nodo expandido **Office\/SharePoint**, seleccione el nodo **Office Agregar\-INS**.  
  
4.  En la lista de plantillas de proyecto, seleccione **Libro de Excel 2010** o el proyecto **Libro 2013 de Excel**.  
  
5.  En el cuadro **Nombre**, escriba **AdventureWorksReport**.  No modifique la ubicación.  
  
6.  Haga clic en **Aceptar**.  
  
     Se abre el **Asistente para proyectos de Visual Studio Tools para Office**.  
  
7.  Asegúrese de que esté seleccionada la opción **Crear un nuevo documento** y, a continuación, haga clic en **Aceptar**  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el libro **AdventureWorksReport** en el diseñador y agrega el proyecto **AdventureWorksReport** al **Explorador de soluciones**.  
  
## Agregar el conjunto de datos a los orígenes de datos en el proyecto de libro de Excel  
 Para poder mostrar el conjunto de datos en el libro de Excel, es preciso agregarlo primero a los orígenes de datos en el proyecto de libro de Excel.  
  
#### Para agregar el conjunto de datos a los orígenes de datos en el proyecto de libro de Excel  
  
1.  En el **Explorador de soluciones**, haga doble clic en **Sheet1.cs** o **Sheet1.vb** debajo del proyecto **AdventureWorksReport**.  
  
     El libro se abre en el diseñador.  
  
2.  En el menú **Datos**, haga clic en **Agregar nuevo origen de datos**.  
  
     Se abrirá el **Asistente para la configuración de orígenes de datos**.  
  
3.  Haga clic en **Objeto** y, a continuación, haga clic en **Siguiente**.  
  
4.  En la página **Seleccione el objeto que desee enlazar a**, haga clic en **Agregar referencia**.  
  
5.  En la ficha **Proyectos**, haga clic en **AdventureWorksDataSet** y, a continuación, haga clic en **Aceptar**.  
  
6.  Debajo del espacio de nombres **AdventureWorksDataSet** del ensamblado **AdventureWorksDataSet**, haga clic en **AdventureWorksLTDataSet** y, a continuación, haga clic en **Finalizar**.  
  
     Se abre la ventana **Orígenes de datos** y se agrega **AdventureWorksLTDataSet** a la lista de orígenes de datos.  
  
## Crear un control ListObject enlazado a una instancia del conjunto de datos  
 Para mostrar el conjunto de datos en el libro, cree un control <xref:Microsoft.Office.Tools.Excel.ListObject> que esté enlazado a una instancia del conjunto de datos.  Para obtener más información sobre cómo enlazar controles a datos, vea [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
#### Para crear un control ListObject enlazado a una instancia del conjunto de datos  
  
1.  En la ventana **Orígenes de datos**, expanda el nodo **AdventureWorksLTDataSet** debajo de **AdventureWorksDataSet**.  
  
2.  Seleccione el nodo **Producto**, haga clic en la flecha desplegable que aparece y, a continuación, seleccione **ListObject** en la lista desplegable.  
  
     Si no aparece la flecha desplegable, confirme que el libro está abierto en el diseñador.  
  
3.  Arrastre la tabla **Product** hasta la celda A1.  
  
     Se crea un control <xref:Microsoft.Office.Tools.Excel.ListObject> denominado `productListObject` en la hoja de cálculo, a partir de la celda A1.  Al mismo tiempo, se agregan al proyecto un objeto de conjunto de datos denominado `adventureWorksLTDataSet` y una clase <xref:System.Windows.Forms.BindingSource> denominada `productBindingSource`.  El control <xref:Microsoft.Office.Tools.Excel.ListObject> se enlaza a <xref:System.Windows.Forms.BindingSource>, que a su vez se enlaza al objeto de conjunto de datos.  
  
## Agregar el conjunto de datos a la memoria caché de datos  
 Para permitir que código fuera del proyecto de libro de Excel obtenga acceso al conjunto de datos del libro, debe agregar el conjunto de datos a la memoria caché de datos.  Para obtener más información sobre la memoria caché de datos, vea [Datos almacenados en caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md) y [Almacenar datos en caché](../vsto/caching-data.md).  
  
#### Para agregar el conjunto de datos a la memoria caché de datos  
  
1.  En el diseñador, haga clic en **adventureWorksLTDataSet**.  
  
2.  En la ventana **Propiedades**, establezca la propiedad **Modifiers** en **Public**.  
  
3.  Establezca la propiedad **CacheInDocument** en **True**.  
  
## Punto de control  
 Genere y ejecute el proyecto de libro de Excel para asegurarse de que se compile y se ejecute sin errores.  
  
#### Para compilar y ejecutar el proyecto  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **AdventureWorksReport**, elija **Depurar** y, a continuación, haga clic en **Iniciar nueva instancia**.  
  
     Se compila el proyecto y se abre el libro en Excel.  <xref:Microsoft.Office.Tools.Excel.ListObject> en Sheet1 está vacío porque el objeto `adventureWorksLTDataSet` en la memoria caché de datos aún no tiene datos.  En la sección siguiente, utilizará una aplicación de consola para rellenar el objeto `adventureWorksLTDataSet` con datos.  
  
2.  Cierre Excel.  No guarde los cambios.  
  
## Crear un proyecto de aplicación de consola  
 Cree un proyecto de aplicación de consola que utilizará para insertar en el libro los datos contenidos en el conjunto de datos almacenado en memoria caché.  
  
#### Para crear un proyecto de aplicación de consola  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en la solución **AdventureWorksDataSet**, elija **Agregar** y, a continuación, haga clic en **Nuevo proyecto**.  
  
2.  En el panel **Tipos de proyecto**, expanda **Visual C\#** o **Visual Basic** y, a continuación, haga clic en **Windows**.  
  
3.  En el panel **Plantillas**, seleccione **Aplicación de consola**.  
  
4.  En el cuadro **Nombre**, escriba **DataWriter**.  No modifique la ubicación.  
  
5.  Haga clic en **Aceptar**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **DataWriter** al **Explorador de soluciones** y abre el archivo de código **Program.cs** o **Module1.vb**.  
  
## Agregar datos al conjunto de datos almacenado en memoria caché utilizando la aplicación de consola  
 Utilice la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> en la aplicación de consola para rellenar el conjunto de datos almacenado en memoria caché del libro con datos.  
  
#### Para agregar datos al conjunto de datos almacenado en la memoria caché  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **DataWriter** y, a continuación, haga clic en **Agregar referencia**.  
  
2.  En la pestaña **.NET**, seleccione **Microsoft.VisualStudio.Tools.Applications.ServerDocument**.  
  
3.  Haga clic en **Aceptar**.  
  
4.  En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **DataWriter** y, a continuación, haga clic en **Agregar referencia**.  
  
5.  En la ficha **Proyectos**, seleccione **AdventureWorksDataSet** y, a continuación, haga clic en **Aceptar**.  
  
6.  Abra el archivo Program.cs o Module1.vb en el Editor de código.  
  
7.  Agregue la siguiente instrucción **using** \(para C\#\) o **Imports** \(para Visual Basic\) al principio del archivo de código.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#1)]
     [!code-vb[Trin_CachedDataWalkthroughs#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#1)]  
  
8.  Agregue el código siguiente al método `Main`.  Este código declara los siguientes objetos:  
  
    -   Instancias de los tipos `ProductTableAdapter` y `AdventureWorksLTDataSet` que se definen en el proyecto **AdventureWorksDataSet**.  
  
    -   La ruta de acceso al libro AdventureWorksReport en la carpeta de compilación del proyecto **AdventureWorksReport**.  
  
    -   Un objeto <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> que se va a usar para obtener acceso a la memoria caché de datos en el libro.  
  
        > [!NOTE]  
        >  En el código siguiente, se supone que se está utilizando un libro con la extensión de archivo .xlsx.  Si el libro del proyecto tiene una extensión de archivo diferente, modifique la ruta de acceso según proceda.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#3)]
     [!code-vb[Trin_CachedDataWalkthroughs#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#3)]  
  
9. Agregue el siguiente código al método `Main`, después del código que agregó en el paso anterior.  Este código realiza las tareas siguientes:  
  
    -   Rellena el objeto de conjunto de datos con tipo utilizando el adaptador de la tabla.  
  
    -   Utiliza la propiedad <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> de la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para obtener acceso al conjunto de datos almacenado en caché del libro.  
  
    -   Utiliza el método <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> para rellenar el conjunto de datos almacenado en memoria caché con datos del conjunto de datos con tipo local.  
  
     [!code-csharp[Trin_CachedDataWalkthroughs#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/CS/DataWriter/Program.cs#4)]
     [!code-vb[Trin_CachedDataWalkthroughs#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataWalkthroughs/VB/DataWriter/Module1.vb#4)]  
  
10. En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **DataWriter**, elija **Depurar** y, a continuación, haga clic en **Iniciar nueva instancia**.  
  
     El proyecto se compila y la aplicación de consola muestra varios mensajes de estado cuando se rellena el conjunto de datos local y cuando la aplicación guarda los datos en el conjunto de datos almacenado en memoria caché del libro.  Presione ENTRAR para cerrar la aplicación.  
  
## Probar el libro  
 Al abrir el libro, <xref:Microsoft.Office.Tools.Excel.ListObject> muestra ahora los datos que se agregaron al conjunto de datos almacenado en memoria caché utilizando la aplicación de consola.  
  
#### Para probar el libro  
  
1.  Cierre el libro AdventureWorksReport en el diseñador de Visual Studio, si todavía está abierto.  
  
2.  En el Explorador de archivos, abra el libro AdventureWorksReport que se encuentra en la carpeta de compilación del proyecto de **AdventureWorksReport**.  De forma predeterminada, la carpeta de compilación está en una de las ubicaciones siguientes:  
  
    -   %UserProfile%\\Mis documentos\\AdventureWorksReport\\bin\\Debug \(para Windows XP y versiones anteriores\)  
  
    -   %UserProfile%\\Documentos\\AdventureWorksReport\\bin\\Debug \(para Windows Vista\)  
  
3.  Compruebe que <xref:Microsoft.Office.Tools.Excel.ListObject> se rellena con datos después de abrir el libro.  
  
## Pasos siguientes  
 Para obtener más información sobre cómo trabajar con datos almacenados en caché, vea estos temas:  
  
-   Cambiar los datos en un conjunto de datos almacenado en memoria caché sin iniciar Excel.  Para obtener más información, vea [Tutorial: Cambiar los datos almacenados en caché de un libro de trabajo de un servidor](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md).  
  
## Vea también  
 [Tutorial: Cambiar los datos almacenados en caché de un libro de trabajo de un servidor](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md)   
 [Conectar a los datos en aplicaciones de Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)  
  
  