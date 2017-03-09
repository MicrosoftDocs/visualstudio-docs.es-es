---
title: "Tutorial: Pasar datos entre formularios Windows Forms | Microsoft Docs"
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
  - "datos [Visual Studio], pasar entre formularios"
  - "formularios, pasar datos"
  - "tutoriales [Visual Studio], datos"
  - "tutoriales [Windows Forms], datos"
  - "Windows Forms, tutoriales"
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 14
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tutorial: Pasar datos entre formularios Windows Forms
En este tutorial se proporcionan instrucciones paso a paso para pasar datos de un formulario a otro.  Usando las tablas de clientes y pedidos de Northwind, un formulario permitirá a los usuarios seleccionar un cliente y un segundo formulario mostrará los pedidos de los clientes seleccionados.  En este tutorial se muestra cómo crear un método en un formulario que recibe datos del primero formulario.  
  
> [!NOTE]
>  En este tutorial solo se muestra una manera de pasar datos de un formulario a otro.  Hay otras opciones para datos a un formulario, entre ellas las siguientes: puede crear un segundo constructor para recibir datos o puede crear una propiedad pública que se puede establecer con los datos del primer formulario.  
  
 Las tareas ilustradas en este tutorial incluyen:  
  
-   Crear un nuevo proyecto **Aplicación Windows**.  
  
-   Crear y configurar un conjunto de datos con el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png).  
  
-   Seleccionar el control que se va a crear en el formulario al arrastrar elementos desde la ventana **Orígenes de datos**.  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Crear un control enlazado a datos arrastrando elementos desde la ventana **Orígenes de datos** hasta un formulario.  
  
-   Crear un segundo formulario con una cuadrícula para mostrar datos.  
  
-   Crear una consulta de TableAdapter para buscar los pedidos de un cliente determinado.  
  
-   Pasar datos de un formulario a otro.  
  
## Requisitos previos  
 Para completar las tareas de este tutorial, necesitará:  
  
-   Acceso a la base de datos de ejemplo Northwind.  Para obtener más información, vea [Cómo: Instalar bases de datos de ejemplo](../data-tools/how-to-install-sample-databases.md).  
  
## Crear la aplicación para Windows  
  
#### Para crear el nuevo proyecto de Windows  
  
1.  En el menú **Archivo**, cree un nuevo proyecto.  
  
2.  Asigne al proyecto el nombre `PassingDataBetweenForms`.  
  
3.  Seleccione **Aplicación de Windows Forms** y haga clic en **Aceptar**.  Para obtener más información, vea [Aplicaciones cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     El proyecto **PassingDataBetweenForms** se crea y se agrega al **Explorador de soluciones**.  
  
## Crear el origen de datos  
  
#### Para crear el origen de datos  
  
1.  En el menú **Datos**, haga clic en **Mostrar orígenes de datos**.  
  
2.  En la ventana **Orígenes de datos**, seleccione **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.  
  
3.  Seleccione **Base de datos** en la página **Elegir un tipo de datos de origen** y luego haga clic en **Siguiente**.  
  
4.  En la página **Elegir un modelo de base de datos**, compruebe que se ha especificado **Conjunto de datos** y haga clic en **Siguiente**.  
  
5.  En la página **Elegir la conexión de datos**, realice una de las siguientes operaciones:  
  
    -   Si una conexión de datos a la base de datos de ejemplo Northwind está disponible en la lista desplegable, selecciónela.  
  
         O bien  
  
    -   Seleccione **Nueva conexión** para iniciar el cuadro de diálogo **Agregar o modificar conexión**.  
  
6.  Si su base de datos requiere una contraseña y la opción para incluir datos confidenciales está habilitada, seleccione la opción y haga clic en **Siguiente**.  
  
7.  Haga clic en **Siguiente** en la página **Guardar la cadena de conexión en el archivo de configuración de la aplicación**.  
  
8.  Expanda el nodo **Tables** en la página **Elija los objetos de base de datos**.  
  
9. Seleccione las tablas **Customers** y **Orders** y, a continuación, haga clic en **Finalizar**.  
  
     **NorthwindDataSet** se agrega al proyecto y las tablas **Customers** y Orders aparecen en la ventana **Orígenes de datos**.  
  
## Crear el primer formulario \(Form1\)  
 Puede crear una cuadrícula enlazada a datos \(un control <xref:System.Windows.Forms.DataGridView>\) arrastrando el nodo **Customers** desde la ventana **Orígenes de datos** al formulario.  
  
#### Para crear una cuadrícula enlazada a datos en el formulario  
  
-   Arrastre el nodo **Customers** principal desde la ventana **Orígenes de datos** a **Form1**.  
  
     En **Form1** aparecen <xref:System.Windows.Forms.DataGridView> y una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\) para navegar por los registros.  En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
## Crear el segundo formulario \(Form2\)  
  
#### Para crear un segundo formulario al que pasar los datos  
  
1.  En el menú **Proyecto**, elija **Agregar Windows Forms**.  
  
2.  Deje el nombre predeterminado **Form2** y haga clic en **Agregar**.  
  
3.  Arrastre el nodo **Orders** principal desde la ventana **Orígenes de datos** a **Form2**.  
  
     En **Form2** aparecen <xref:System.Windows.Forms.DataGridView> y una barra de herramientas \(<xref:System.Windows.Forms.BindingNavigator>\) para navegar por los registros.  En la bandeja de componentes aparecen [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource> y <xref:System.Windows.Forms.BindingNavigator>.  
  
4.  Elimine **OrdersBindingNavigator** de la bandeja de componentes.  
  
     **OrdersBindingNavigator** desaparece del **Form2**.  
  
## Agregar una consulta de TableAdapter al Form2 para cargar pedidos del cliente seleccionado en el Form1  
  
#### Para crear una consulta de TableAdapter  
  
1.  Haga doble clic en el archivo **NorthwindDataSet.xsd**, en el **Explorador de soluciones**.  
  
2.  Haga clic con el botón secundario en **OrdersTableAdapter** y seleccione **Agregar consulta**.  
  
3.  Deje la opción predeterminada **Usar instrucciones SQL** y haga clic en **Siguiente**.  
  
4.  Deje la opción predeterminada **SELECT que devuelve filas** y haga clic en **Siguiente**.  
  
5.  Agregue una cláusula WHERE a la consulta para que devuelva `Orders` en función del `CustomerID`.  La consulta debe ser similar a lo siguiente:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Compruebe que la sintaxis de los parámetros sea correcta para su base de datos.  Por ejemplo, en Microsoft Access, la cláusula WHERE tendría el siguiente aspecto: `WHERE CustomerID = ?`.  
  
6.  Haga clic en **Siguiente**.  
  
7.  En **Rellenar un DataTable**, en **Nombre del método**, escriba `FillByCustomerID`.  
  
8.  Desactive la opción **Devolver un DataTable** y haga clic en **Siguiente**.  
  
9. Haga clic en **Finalizar**.  
  
## Crear un método en Form2 al que pasar datos  
  
#### Para crear un método al que pasar datos  
  
1.  Haga clic con el botón secundario en **Form2** y seleccione **Ver código** para abrir **Form2** en el **Editor de código**.  
  
2.  Agregue el código siguiente a **Form2** después del método `Form2_Load`:  
  
     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-cs[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]  
  
## Crear un método en Form1 para pasar datos y mostrarlos en Form2  
  
#### Para crear un método para pasar datos a Form2  
  
1.  En **Form1**, haga clic con el botón secundario en la cuadrícula de datos Customer y, después, haga clic en **Propiedades**.  
  
2.  En la ventana **Propiedades**, haga clic en **Eventos**.  
  
3.  Haga doble clic en el evento **CellDoubleClick**.  
  
     Aparece el editor de código.  
  
4.  Actualice la definición del método para que coincida con el ejemplo siguiente:  
  
     [!code-cs[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]  
  
## Ejecutar la aplicación  
  
#### Para ejecutar la aplicación  
  
-   Presione F5 para ejecutar la aplicación.  
  
-   Haga doble clic en un registro de cliente en **Form1** para abrir **Form2** con los pedidos del cliente.  
  
## Pasos siguientes  
 Dependiendo de los requisitos de la aplicación, existen varios pasos que se pueden realizar después de pasar los datos de un formulario a otro.  Entre las mejoras que podría realizar se incluyen:  
  
-   Modificar el conjunto de datos agregando o quitando objetos de la base de datos.  Para obtener más información, vea [Cómo: Editar un conjunto de datos](../Topic/How%20to:%20Edit%20a%20Dataset.md).  
  
-   Agregar funcionalidad para guardar los datos de nuevo en la base de datos.  Para obtener más información, vea [Cómo: Guardar cambios de un conjunto de datos en una base de datos](../data-tools/how-to-save-dataset-changes-to-a-database.md).  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)