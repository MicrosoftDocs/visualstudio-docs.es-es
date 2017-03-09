---
title: "Tutorial: Guardar datos con los m&#233;todos DBDirect de un TableAdapter | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], guardar"
  - "datos [Visual Studio], TableAdapter"
  - "guardar datos, tutoriales"
  - "TableAdapters, tutoriales"
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Guardar datos con los m&#233;todos DBDirect de un TableAdapter
Este tutorial proporciona instrucciones detalladas para ejecutar instrucciones SQL directamente en una base de datos usando los métodos DBDirect de un TableAdapter.  Los métodos DBDirect de un TableAdapter proporcionan un nivel exhaustivo de control sobre las actualizaciones de la base de datos.  Con ello, puede ejecutar instrucciones SQL específicas y procedimientos almacenados llamando a los métodos `Insert`, `Update` y `Delete` individuales según necesite su aplicación, en lugar del método `Update` sobrecargado que realiza las instrucciones UPDATE, INSERT y DELETE en una llamada\).  
  
 Durante este tutorial aprenderá a:  
  
-   Crear una nueva **aplicación para Windows**.  
  
-   Crear y configurar un conjunto de datos con el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Seleccionar el control que se va a crear en el formulario al arrastrar elementos desde la ventana **Orígenes de datos**.  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Crear un formulario enlazado a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta el formulario.  
  
-   Agregar métodos para acceder directamente a la base de datos y realizar inserciones, actualizaciones y eliminaciones directamente en la base de datos.  
  
## Requisitos previos  
 Para poder completar este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind.  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear una aplicación para Windows  
 El primer paso es crear una **Aplicación para Windows**.  
  
#### Para crear el nuevo proyecto de Windows  
  
1.  En Visual Studio, en el menú **Archivo** cree un nuevo **Proyecto**.  
  
2.  Asigne al proyecto el nombre TableAdapterDbDirectMethodsWalkthrough.  
  
3.  Seleccione **Aplicación para Windows** y haga clic en **Aceptar**.  Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     Se crea el proyecto **TableAdapterDbDirectMethodsWalkthrough** y se agrega al **Explorador de soluciones**.  
  
## Crear un origen de datos de su base de datos  
 En este paso se usa el **Asistente para configuración de orígenes de datos** para crear un origen de datos basado en la tabla `Region` de la base de datos de ejemplo Northwind.  Debe tener acceso a la base de datos de ejemplo Northwind para crear la conexión.  Para obtener información sobre la configuración de la base de datos de ejemplo Northwind, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
#### Para crear el origen de datos  
  
1.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos**.  
  
2.  En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En la página **Elegir la conexión de datos** realice una de las siguientes operaciones:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.  
  
5.  Si su base de datos requiere una contraseña, seleccione la opción para incluir datos confidenciales y haga clic en **Siguiente**.  
  
6.  Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.  
  
7.  Expanda el nodo **Tables** en la página **Elija los objetos de base de datos**.  
  
8.  Seleccione la tabla `Region` y haga clic en **Finalizar**.  
  
     **NorthwindDataSet** se agrega al proyecto y la tabla `Region` aparece en la ventana **Orígenes de datos**.  
  
## Agregar controles al formulario para mostrar los datos  
 Cree los controles enlazados a datos arrastrando elementos desde la ventana **Orígenes de datos** al formulario.  
  
#### Para crear controles enlazados a datos en el formulario de Windows Forms  
  
-   Arrastre el nodo **Region** principal desde la ventana **Orígenes de datos** hasta el formulario.  
  
     En el formulario aparecen un control <xref:System.Windows.Forms.DataGridView> y una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\) para navegar por los registros.  En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [RegionTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
#### Para agregar botones que llamarán a los métodos DbDirect de TableAdapter  
  
1.  Arrastre tres controles <xref:System.Windows.Forms.Button> desde el **Cuadro de herramientas** hasta **Form1** \(debajo de **RegionDataGridView**\).  
  
2.  Establezca las propiedades **Nombre** y **Texto** en cada botón.  
  
    |Nombre|Texto|  
    |------------|-----------|  
    |`InsertButton`|Insertar|  
    |`UpdateButton`|Actualizar|  
    |`DeleteButton`|Eliminar|  
  
#### Para agregar código para insertar nuevos registros en la base de datos  
  
1.  Haga doble clic en **InsertButton** para crear un controlador para el evento de clic y abrir el formulario en el editor de código.  
  
2.  Reemplace el controlador de evento `InsertButton_Click` con el código siguiente:  
  
     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-cs[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]  
  
#### Para agregar código para actualizar los registros de la base de datos  
  
1.  Haga doble clic en **UpdateButton** para crear un controlador para el evento de clic y abrir el formulario en el editor de código.  
  
2.  Reemplace el controlador de evento `UpdateButton_Click` con el código siguiente:  
  
     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-cs[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]  
  
#### Para agregar código para eliminar registros de la base de datos  
  
1.  Haga doble clic en **DeleteButton** para crear un controlador para el evento de clic y abrir el formulario en el editor de código.  
  
2.  Reemplace el controlador de evento `DeleteButton_Click` con el código siguiente:  
  
     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-cs[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]  
  
## Ejecutar la aplicación  
  
#### Para ejecutar la aplicación  
  
-   Presione F5 para ejecutar la aplicación.  
  
-   Haga clic en el botón **Insertar** y compruebe que el nuevo registro se muestra en la cuadrícula.  
  
-   Haga clic en el botón **Actualizar** y compruebe que el registro se actualiza en la cuadrícula.  
  
-   Haga clic en el botón **Eliminar** y compruebe que el registro se quita de la cuadrícula.  
  
## Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, hay varios pasos que pueden realizarse después de crear un formulario enlazado a datos.  Entre las mejoras que podría realizar se incluyen:  
  
-   Agregar funcionalidad de búsqueda al formulario.  Para obtener más información, vea [Cómo: Agregar una consulta parametrizada a una aplicación de Windows Forms](../Topic/How%20to:%20Add%20a%20Parameterized%20Query%20to%20a%20Windows%20Forms%20Application.md).  
  
-   Agregar otras tablas al conjunto de datos seleccionando **Configurar DataSet con el asistente** en la ventana **Orígenes de datos**.  Puede agregar controles que muestren los datos relacionados arrastrando los nodos relacionados al formulario.  Para obtener más información, vea [Cómo: Mostrar datos relacionados en una aplicación de Windows Forms](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md).  
  
## Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: Obtener acceso directamente a la base de datos con un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Cómo: Crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Cómo: Guardar los datos de un objeto en una base de datos](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)